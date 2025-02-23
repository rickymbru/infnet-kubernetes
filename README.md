# Projeto da disciplina - Administração de Containers com Docker e Kubernetes [25E1_2]

## Pré-requisitos:
* [AWS Client](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
* [Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)
* Arquivo cred.txt com as credencias obtidas na AWS Academy, neste caso utilizamos o Laboratorio: Criação de um Aplicativo Web Dimensionável e Altamente Disponível.

## Configuração do Cluster Kubernetes
### Clonar repositório:
```bash
    git clone git@github.com:rickymbru/infnet-kubernetes.git
    cd infnet-kubernetes
```
### Inicializar Terraform**: 
```bash
terraform init 
```
### Deployment**:
```bash
terraform apply
```    
### Validar a saída do Cluster
```bash
terraform output
```
### Instalar as dependencias do Longhorn
```bash
sudo kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/v1.8.0/deploy/longhorn.yaml
```
#### Verificar a instalação do Longhorn
```bash
sudo kubectl get pods \
--namespace longhorn-system \
--watch
```
### Criando o namespace wp-projeto:
```bash
sudo kubectl apply -f namespace.yml
```
### Criando o ConfigMap para o wordpress e mysql
 ```bash
sudo kubectl apply -f configmap.yaml
```
### Criando secrets
 ```bash
sudo kubectl apply -f secret.yml
```
### Criar PVC do wordpress
 ```bash
sudo kubectl apply -f pvc_wordpress.yaml
```
### Criar statefullset mysql
 ```bash
sudo kubectl apply -f statefullset.yaml
```
### Criar deployment wordpress
 ```bash
sudo kubectl apply -f deployment.yml
```
### Criar service wordpress
 ```bash
sudo kubectl apply -f svc_wordpress.yml
```
### Criar service mysql
 ```bash
sudo kubectl apply -f svc_mysql_headless.yml
```
