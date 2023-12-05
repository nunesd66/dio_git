# Versionamento de Código com Git e GitHub

> Curso oferecido pela plataforma DIO e apresentado por @elidianaandrade.

> Repositório de referência.

> [Documentação do GitHub](https://docs.github.com/pt)

## :receipt: Sumário

1. [O que é Versionamento de Código ?](#versionamento)
2. [O que é Git ?](#git)
3. [O que é GitHub ?](#github)
4. [2FA - Autenticação de 2 Fatores](#2fa)
5. [Configurações do Git](#config)
6. [Autenticando via Token](#token)
7. [Autenticando via Chave SSH](#ssh)
8. [Criando e Clonando Repositórios](#criarclonar)
9. [Markdown](#md)
10. [Desfazendo alterações no Repositório Local](#rollback)
11. [Repositório Remoto - Enviando e baixando alterações](#remote)
12. [Branches](#branches)
13. [Outros comandos](#comandos)
14. [Dicas e materiais de apoio](#dicas)

## 1. O que é Versionamento de Código ? <a id="versionamento"></a>

> O versionamento de código é usado durante a construção de uma aplicação tecnológica, onde novas correções e implementações são criadas diariamente. Por isso é necessário trabalhar com o auxílio de ferramentas que ajudam no registro dessas modificações, indicando quem fez a mudança, quando e o que foi alterado.

## 2. O que é Git ? <a id="git"></a>

> Git é um sistema de controle de versões distribuído, usado principalmente no desenvolvimento de software, mas pode ser usado para registrar o histórico de edições de qualquer tipo de arquivo. É um projeto de código aberto maduro e com manutenção ativa desenvolvido em 2005 por Linus Torvalds, o famoso criador do kernel do sistema operacional Linux. Um número impressionante de projetos de software depende do Git para controle de versão, incluindo projetos comerciais e de código-fonte aberto.

## 3. O que é GitHub ? <a id="github"></a>

> GitHub é uma plataforma de hospedagem de código-fonte e arquivos com controle de versão usando o Git. Ele permite que programadores, utilitários ou qualquer usuário cadastrado na plataforma contribuam em projetos privados e/ou Open Source de qualquer lugar do mundo. 
 
## 4. 2FA - Autenticação de 2 Fatores <a id="2fa"></a>

### O que é ?

> Camada de segurança adicional contendo 2 etapas, sua senha e uma etapa adicional com base no que foi configurado/escolhido.

### Como implementar isso ?

> página do GitHub > Canto superior direito (avatar) > Settings > Password and authentication > Enable two-factor authentication > `Usar pelo celular um aplicativo de autenticação (Microsoft Authenticator ou outro) para ler o QRCode e adicionar o GitHub nesse aplicativo`.

> Na mesma tela do QRCode, aparece algo como `enter this text code`, para adicionar o número de uma operadora celular na autenticação de 2 etapas, para ter a 2ª etapa como código enviado por SMS (mensagem de texto).

## 5. Configurações do Git <a id="config"></a>

### mostrar informações dos comandos de configuração

> `$ git config`

### incliur globalmente o nome e o email do usuário

> `$ git config --global user.name "seu nome"`

> `$ git config --global user.email "seu email"`

### visualizar o nome e o email do usuário

> `$ git config user.name`

> `$ git config user.email`

### alterar globalmente nome da branch origin

> `$ git config --global init.defaultBranch novo_nome`

### visualizar nome da branch origin

> `$ git config init.defaultBranch`

### visualizar todas as configurações globais adicionadas

> `$ git config --global --list`

## 6. Autenticando via Token <a id="token"></a>

> Token de segurança do GitHub para ser usado como uma senha de autenticação.

### Como gerar um token ?

> página do GitHub > Canto superior direito (avatar) > Settings > Developer settings > Personal access tokens > Tokens (classic) > Generate new token > Generate new token (classic) > `Configure o token`:
> - Note - descrição do token;
> - Expiration - tempo que o tempo vai expirar;
> - Select Scopes - selecionar as permissões do token;
> 
>  Generate token > `Copie o token e salve essa informação, pois esse código só é visto uma vez`

### Salvar credenciais do token no ambiente local para usar o GitHub sem ter que sempre autenticar

> `$ git config --global credential.helper store`

### Visualizar credenciais salvas

> `$ git config --global credential.helper`

### Caminho onde foi salvo as informações de credenciais

> `$ git config --global --show-origin credential.helper`

## 7. Autenticando via Chave SSH <a id="ssh"></a>

> Protocolo de rede onde a máquina local e o GitHub se conectem de forma segura e criptografada.

### Verificar se há chave SSH

> `$ ls -al ~/.ssh`

### Gerar uma nova chave SSH

> `$ ssh-keygen -t ed25519 -C "your_email@example.com"`

> Depois no terminal, aparece para digitar o caminho onde será salva a chave, caso queira usar o padrão, deixe em branco e aperte `ENTER`.

> Depois ele pede uma passphrase, ou seja, uma senha. Informe a senha e confirme.

> `$ eval "$(ssh-agent -s)"` // starta o ssh-agente e retorna um pid.

> `$ ssh-add ~/.ssh/id_ed25519` // para adicionar a chave privada ao ssh agent, nesse passo é requerido o passphrase, onde caso sucesso uma mensagem de confirmação aparece.

### Como gerar uma Chave SSH no GitHub ?

> página do GitHub > Canto superior direito (avatar) > Settings > SSH and GPG keys > New SSH key > `preencher o Title com um título, Key type como Authentication Key e em Key, é necessário colar a chave pública`.

> `$ cat ~/.ssh/id_ed25519.pub` // exibe a chave pública para colar no campo `Key`.

## 8. Criando e Clonando Repositórios <a id="criarclonar"></a>

#### Para criar um repositório local, entre na pasta será iniciado o git

> `$ git init`

### Para clonar um repositório do git na máquina local

> `Entre na página do repositório` > Code > `Copie a url`

> `$ git clone url_copiado` //ou...
> 
> `$ git clone url_copiado nome_pasta` // Caso deseje alterar o nome da pasta no repositório local.

### Alterar ou atribuir repositório remoto

> `Entre na página do repositório` > Code > `Copie a url`

> `$ git remote add origin url_repositorio_remoto`

### Clonar determinada branch

> `$ git clone url -- branch nome_branch --single-branch`

### Mostrar o status atual do repositório git local

> `git status`

### Adicionar alterações para serem "commitadas"

> `$ git add .` // para adicionar todas as alterações
>
> `$ git add arquivo_tal` // para adicionar apenas uma alterações específica

### "Commitar" alterações que foram adicionadas

> `$ git commit -m "mensagem do commit"`

### Verificar histórico de commits

> `$ git log`

### Ignorar determinada pasta

> `$ echo nome_pasta/ > .gitignore`

### Adicionar pastas vazias nos commits

> `$ touch nome_pasta/.gitkeep`

## 9. Markdown <a id="md"></a>

> Linguagem de marcação, como HTML, bastante usada em arquivos README.md do GitHub, que são arquivos de apresentações e afins.

> Existem diversos sites de visualização de arquivos markdown, como vários tutoriais também, inclusive na [documentação](https://docs.github.com/pt/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github) do GitHub.

## 10. Desfazendo alterações no Repositório Local <a id="rollback"></a>

### Remover versionamento da pasta

> `$ rm -rf .git`

### Descarta alterações de determinado arquivo antes do último commit

> `$ git restore nome_arquivo`

### Corrigir mensagem do último commit

> `$ git commit -amend -m "mensagem de correção"`

### Desfazer último commit

> `$ git reset --soft codigo_commit` // desfaz e adiciona os arquivos em stage-area (adicionados para commitar).
>
> `$ git reset --mixed codigo_commit` // o --mixed é opcional, desfaz e adiciona os arquivos em untracked (arquivos não adicionados).
>
> `$ git reset --hard codigo_commit` // ignora todos os arquivos e vai para o estado de determinado commit.

### Histórico detalhado de alterações, contendo branchs alteradas

> `$ git reflog`

### Remover determinado arquivo da stage-area (adicionado na área de preparação)

> `$ git reset nome_arquivo` // ou...
>
> `$ git restore --staged nome_arquivo`

## 11. Repositório Remoto - Enviando e baixando alterações <a id="remote"></a>

### Adicionando origin no ambiente local

> `$ git add origin url_repo_github`

### Forçar renomear o nome da branch principal para "main"

> `$ git branch -M main`

### Enviar alterações commitadas do local para o remoto

> `$ git push -u origin main`

### Atualizar o repositório local com base no remoto

> `$ git pull`

## 12. Branches <a id="branches"></a>

> Ramificações de uma outra branch, normalmente a main ou master, que tem como objetivo acumular commits afim de evitar conflitos em cada envio, sendo necessário apenas uma resolução de conflitos, que é quando une essa ramificação pararela a outra.

### Criando uma branch a partir da branch atual

> `$ git checkout -b nome_nova_branch`

### Listando branches

> `$ git branch`

### Trocando de branch

> `$ git checkout nome_branch`

### Mostrando o último commit de cada branch

> `$ git branch -v`

### Mescla a branch atual com outra

> `$ git merge nome_branch_mergear`

### Excluir uma branch

> `$ git branch -d nome_branch_excluir`

## 13. Outros comandos <a id="comandos"></a>

### Baixa as alterações do repositório remoto para o repositório local sem mesclar

> `$ git fetch`

### Visualizar as diferenças entre 2 branches

> `$ git diff branch_1 branch_2`

### Mestra alterações da branch atual com a branch selecionada

> `$ git merge branch_remota`

### Clonar apenas uma branch de um repositório remoto

> `$ git clone url_projeto_github --branch nome_branch --single-branch`

### Arquivar modificações (para não serem herdadas caso crie uma nova branch a partir da atual)

> `$ git stash`

### Visualizar modificações arquivadas

> `$ git stash list`

### Recuperar modificações arquivadas

> `$ git stash apply`

### Limpar modificações arquivadas

> `$ git stash pop`

## 14. Dicas e materiais de apoio <a id="dicas"></a>

- [Repositório da autora do curso - PT-BR](https://github.com/elidianaandrade/dio-curso-git-github)
- [Site Oficial do Git - EN]( https://git-scm.com/)
- [Documentação Oficial do GitHub - PT-BR](https://docs.github.com/)
- [Blog Oficial do GitHub - EN](https://github.blog/)
- [Artigo Autenticação com Token - EN](https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/)
- [Artigo Acidente DDoS - EN](https://github.blog/2018-03-01-ddos-incident-report/)
- [Artigo Venda do GitHub - EN](https://news.microsoft.com/2018/06/04/microsoft-to-acquire-github-for-7-5-billion/)
- [Artigo 2FA - EN](https://github.blog/2023-03-09-raising-the-bar-for-software-security-github-2fa-begins-march-13/)
- [Palestra Linus Torvalds sobre Git - EN](https://www.youtube.com/watch?v=4XpnKHJAok8)
- [Livro Oficial Pro Git v.2 - EN](https://git-scm.com/book/en/v2)
