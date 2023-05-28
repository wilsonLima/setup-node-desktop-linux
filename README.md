setup-node-desktop-linux
=========

Role do Ansible com passos para a instalação de pacotes de Desenvolvimento NodeJS em Desktop Linux.

Distribuições Suportadas pela Role
------------

- Fedora 37 ou inferior
- Linux Mint LMDE 5 ou superior
- Linux Mint 21 ou inferior
- openSUSE Leap 15.4 ou superior
- openSUSE Tumbleweed
- Ubuntu 22.10 ou superior


Tags da Role 
--------------

- main: Tag a ser utilizada em conjunto com outras tags, se alguma tag for especificada no comando.
  
- repo: Inclui todos os repositórios da role no Sistema.

- nodejs: Instala os componentes do Nodejs.
- eslint: Instala o componentes eslint via NPM.
- gitignore: Instala o componentes gitignore via NPM.


Variáveis da Role 
--------------

- nodejs_version: Versão do Nodejs (Válida somente para distribuições baseados no Debian e Red Hat). Possíveis valores são 8, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19 e 20, o valor padrão: 20.


Dependências da Role 
--------------

Linux Mint e Ubuntu:

- openssh-server. Ex.: sudo apt install openssh-server


Exemplo de Inventario
----------------

Exemplo de arquivo de hosts: pasta_invetario/hosts

    [NOME]
    IP ansible_connection=ssh ansible_ssh_user=USUARIO ansible_ssh_pass=SENHA_URUARIO ansible_become_pass=SENHA_ROOT


Especificar interpretador python 3: pasta_invetario/group_vars/all

    ansible_python_interpreter: "/usr/bin/python3"


Exemplo de Playbook
----------------

Exemplo de uso da Role, com as configurações padrão:

    - hosts: desktop
      roles:
         - setup-node-desktop-linux

Exemplo de uso da Role com variáveis:

    - hosts: desktop
      roles:
         - { role: setup-node-desktop-linux, nodejs_version: '13' }


Exemplo de Comandos
----------------

Comando para executar todas as tasks:

    ansible-playbook -i <caminho_inventario> <caminho_playbook>

Comando para executar a tag "eslint" (em caso de uso de tags, a tag "main" é obrigatória):

    ansible-playbook -i <caminho_inventario> <caminho_playbook> --tags "main, eslint"


License
-------

MIT