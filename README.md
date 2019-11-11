# course-alura-kubernetes

Result of [Alura](https://alura.com.br) courses:

- **[Kubernetes: Introdução a orquestração de containers](https://cursos.alura.com.br/course/kubernetes)**

## Locally required facilities

- [Minikube](https://minikube.sigs.k8s.io/)

## How to up

- DB

```bash
kubectl create -f .\db\permissoes-banco.yaml
kubectl create -f .\db\statefulset-banco.yaml
kubectl create -f .\db\servico-banco.yaml

kubectl get pods
kubectl exec -it [nome do pod] sh
mysql -u root
```

```sql
use loja
create table produtos (id integer auto_increment primary key, nome varchar(255), preco decimal(10,2));
alter table produtos add column usado boolean default false;
alter table produtos add column descricao varchar(255);
create table categorias (id integer auto_increment primary key, nome varchar(255));
insert into categorias (nome) values ("Futebol"), ("Volei"), ("Tenis");
alter table produtos add column categoria_id integer;
update produtos set categoria_id = 1;
```

- Application

```bash
kubectl create -f .\app\deployment-aplicacao.yaml
kubectl create -f .\app\servico-aplicacao.yaml

minikube get service
```

> Access URL for `servico-aplicacao`.
