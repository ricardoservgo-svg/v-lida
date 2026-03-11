<!DOCTYPE html><html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Controle de Validade - Supermercado</title>
<style>
body{font-family:Arial;background:#f4f6f8;margin:20px}
h1{color:#333}
.container{max-width:900px;margin:auto}
.card{background:white;padding:20px;margin-bottom:20px;border-radius:10px;box-shadow:0 2px 5px rgba(0,0,0,0.1)}
input,button{padding:8px;margin:5px}
table{width:100%;border-collapse:collapse}
th,td{padding:10px;border-bottom:1px solid #ddd;text-align:left}
.alert{color:red;font-weight:bold}
.warning{color:orange;font-weight:bold}
.ok{color:green}
</style>
</head>
<body>
<div class="container">
<h1>Controle de Validade de Produtos</h1><div class="card">
<h3>Cadastrar Produto</h3>
<input id="nome" placeholder="Nome do Produto">
<input id="lote" placeholder="Lote">
<input id="quantidade" type="number" placeholder="Quantidade">
<input id="validade" type="date">
<button onclick="adicionarProduto()">Adicionar</button>
</div><div class="card">
<h3>Produtos</h3>
<table>
<thead>
<tr>
<th>Produto</th>
<th>Lote</th>
<th>Quantidade</th>
<th>Validade</th>
<th>Status</th>
<th>Ação</th>
</tr>
</thead>
<tbody id="tabela"></tbody>
</table>
</div>
</div><script>
let produtos = JSON.parse(localStorage.getItem('produtos')) || [];

function salvar(){
localStorage.setItem('produtos',JSON.stringify(produtos));
}

function statusValidade(data){
let hoje = new Date();
let validade = new Date(data);
let diff = (validade-hoje)/(1000*60*60*24);

if(diff < 0) return '<span class="alert">Vencido</span>';
if(diff <= 7) return '<span class="alert">Vence em breve</span>';
if(diff <= 30) return '<span class="warning">Próximo do vencimento</span>';
return '<span class="ok">OK</span>';
}

function adicionarProduto(){
let nome=document.getElementById('nome').value;
let lote=document.getElementById('lote').value;
let quantidade=document.getElementById('quantidade').value;
let validade=document.getElementById('validade').value;

if(!nome||!validade) return alert('Preencha os campos');

produtos.push({nome,lote,quantidade,validade});
salvar();
render();
}

function remover(i){
produtos.splice(i,1);
salvar();
render();
}

function render(){
let tabela=document.getElementById('tabela');
tabela.innerHTML='';

produtos.forEach((p,i)=>{
let tr=document.createElement('tr');
tr.innerHTML=`
<td>${p.nome}</td>
<td>${p.lote}</td>
<td>${p.quantidade}</td>
<td>${p.validade}</td>
<td>${statusValidade(p.validade)}</td>
<td><button onclick="remover(${i})">Excluir</button></td>
`;

tabela.appendChild(tr);
});
}

render();
</script></body>
</html>