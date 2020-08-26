# Ansible ELK - Roles

## Instalação Ansible
### Adicionar repositorio do Ansible
<pre>
sudo apt-add-repository ppa:ansible/ansible
</pre>

### Atualiza os pacotes
<pre>sudo apt update</pre>

### Install Ansible
<pre>sudo apt install ansible</pre>

<br/>

## Entendo a estrutura de pastas

    ./
    ├── invetory
    │   └── invetory.yml
    ├── roles
    │    └── role
    │        ├── defaults
    │        │   └── main.yml
    │        ├── files
    │        |   └── *.rpm | *.tar.gz
    │        ├── tasks
    │        |   └── main.yml
    │        └── templates  
    │            ├── template.yml
    │            ├── template.service.j2
    │            ├── jvm.options.j2 
    │            └── sysctl.conf.j2 
    └── main.yml

Esse é um exemplo de como nossa estrutura de arquivos se comporta:

* invetory: aqui se encontra os arquivos de hosts, a qual, o Ansible de executar suas tarefas;

* roles: aqui se encontra as regras que devém ser aplicadas a um terminado host, cada regra deve ser separa em sua pasta, podendo contem a seguinte configurações de pastas dentro dela;
    * defaults: aqui se encontra os arquivos com as variaveis de nossa regra - arquivo padrão main.yml;
    * files: aqui se encontra os arquivos a serem transferidos para os hosts configurados;
    * tasks: aqui se encontra os arquivos com as tarefas a serem executadas nos hosts configurados;
    * templates: aqui se encontra os templates que serem transferidos para o servidor, os templates podem ser. Podendo ser escrito com .yaml | .yml, como utilizando .j2 (Jinja Template Engine) - arquivo padrão main.yml;
        
        **Recomendações**: arquivos que não são terminados por .yaml | .yml, devem optar por .j2, exemplo jvm.options.j2, isso facilita a configuração do arquivo. Ao transferir o arquivo, o Ansible retira o .j2, deixando somente o formato original do arquivo.
    

* main.yml: aqui se encontra nosso playbook, com seus hosts, roles e variaveis. Esse arquivo será confrontado com o arquivo escolhido em inventory(hosts).

<br/>

## Não se esqueça de conferir nosso repositorio para ver os exemplos citados acima!

<br/>

## Executando o playbook
Após, configurar o seu main.yml na raiz desse projeto, execute o com o seguinte comando:
<pre>sudo ansible-playbook main.yml -i inventory/inventory.yml</pre>