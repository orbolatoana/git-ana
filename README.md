# 🧩 Aula Prática – Git Local (sem GitHub)

## 🎯 Objetivo
Aprender a utilizar o **Git** localmente para versionar projetos, criando commits, branches e manipulando o histórico de forma segura.

---

## 🧱 1. Configuração inicial

Esses comandos configuram o nome e o e-mail do usuário (necessário para registrar os commits).

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@exemplo.com"
git config --global core.editor "code --wait"   # Define o VS Code como editor padrão (opcional)
git config --list                                # Verifica as configurações atuais
```

Configura seu nome, e-mail e editor de texto no Git, essenciais para registrar quem fez as alterações e escolher a ferramenta para editar mensagens de commit.

---

## 📂 2. Criar e iniciar um repositório

```bash
mkdir meu_projeto
cd meu_projeto
git init
```

> O comando `git init` cria um repositório local, gerando a pasta oculta `.git`.

Cria uma pasta para o projeto e inicia um repositório Git dentro dela, gerando a pasta oculta .git que vai armazenar todo o histórico de versões.

---

## 🏷️ 3. Alterar a branch padrão de `master` para `main`

Por padrão, o Git pode criar a branch inicial como **master**.  
Para padronizar e seguir boas práticas, altere para **main**:

```bash
git branch -m master main
```

Se quiser definir **main** como padrão para novos repositórios:

```bash
git config --global init.defaultBranch main
```

Renomeia a branch padrão de master para main e define main como padrão para novos repositórios.

---

## 📄 4. Criar arquivos e verificar status

```bash
echo "Meu primeiro arquivo" > readme.txt
git status
```

> `git status` mostra arquivos novos, modificados ou prontos para commit.

Cria arquivos e usa o comando git status para verificar quais mudanças foram feitas no repositório.

---

## 🧺 5. Adicionar arquivos à área de staging

```bash
git add readme.txt       # adiciona um arquivo específico
git add .                # adiciona todos os arquivos do diretório
git status
```

> A área de staging é onde os arquivos ficam “preparados” antes do commit.

Usa git add para adicionar arquivos à área de staging, preparando-os para o commit.

---

## 💾 6. Fazer o primeiro commit

```bash
git commit -m "Primeiro commit - adiciona readme.txt"
```

> Um commit é o “salvamento” oficial no histórico do repositório.

Usa git commit para registrar as mudanças feitas no repositório com uma mensagem explicativa.

---

## 🔍 7. Ver histórico e detalhes

```bash
git log
git log --oneline
git show
```

> Use `--oneline` para visualizar um resumo simplificado.

Usa git log para visualizar o histórico de commits e git show para ver detalhes de um commit específico.

---

## ✏️ 8. Editar arquivos e registrar mudanças

```bash
echo "Adicionando nova linha" >> readme.txt
git status
git diff
git add readme.txt
git commit -m "Atualiza readme.txt com nova linha"
```

> `git diff` mostra as diferenças entre a versão atual e a anterior.

Faz modificações, usa git diff para comparar as versões e realiza novos commits para registrar as mudanças.

---

## ♻️ 9. Desfazer mudanças

```bash
git restore readme.txt              # descarta mudanças não adicionadas
git restore --staged readme.txt     # remove da área de staging
```

> Ideal para corrigir erros antes de um commit.

Usa git restore para descartar alterações não comitadas ou remover arquivos da área de staging.

---

## 🌿 10. Criar e alternar entre branches

```bash
git branch                         # lista branches
git branch nova_funcionalidade     # cria nova branch
git switch nova_funcionalidade     # muda para ela
```

> Cada branch é uma linha independente de desenvolvimento.

Cria novas branches para trabalhar em funcionalidades separadas e alterna entre elas com git switch.

---

## 🧬 11. Fazer commits em outra branch

```bash
echo "Nova feature" > feature.txt
git add feature.txt
git commit -m "Adiciona nova feature"
```

Trabalha e faz commits em uma branch separada, sem afetar a branch principal.

---

## 🔀 12. Voltar e mesclar mudanças

```bash
git switch main
git merge nova_funcionalidade
```

> Junta as alterações da branch `nova_funcionalidade` na `main`.

Usa git merge para integrar as alterações de uma branch no main ou em outra branch.

---

## 🗑️ 13. Excluir branches locais

```bash
git branch -d nova_funcionalidade
```

Após mesclar, usa git branch -d para excluir branches locais que não são mais necessárias.

---

## 🧹 14. Ignorar arquivos com `.gitignore`

Crie um arquivo chamado `.gitignore` e adicione:

```
*.log
*.tmp
node_modules/
```

Depois:

```bash
git add .gitignore
git commit -m "Adiciona arquivo .gitignore"
```

Cria um arquivo .gitignore para evitar que arquivos temporários ou desnecessários sejam versionados.

---

## 🧠 15. Visualizar informações úteis

```bash
git status
git log --oneline --graph --decorate
git diff
git show HEAD
```

> `--graph` mostra o histórico com ramificações visualmente.

Usa comandos como git status, git log --graph e git diff para ver o status do repositório, o histórico de commits e as diferenças entre versões.

---

## 💡 16. Exemplo de fluxo completo

```bash
git init
echo "Aula prática Git local" > readme.txt
git add .
git commit -m "Primeiro commit"
git branch dev
git switch dev
echo "Nova versão em desenvolvimento" >> readme.txt
git add .
git commit -m "Atualiza versão dev"
git switch main
git merge dev
git log --oneline --graph
```

Mostra um fluxo de trabalho do início ao fim, desde a criação de um repositório até a criação de branches, commits e merge de funcionalidades.

---

## 📘 Créditos

Material criado para fins educacionais na aula prática de **Git Local**,  
ministrada por *Anderson R. M. Gomes* 🧑‍🏫

---

**🚀 Próximos passos:**  
Na próxima aula, você aprenderá a conectar este repositório local ao GitHub com os comandos `git remote`, `git push` e `git pull`.

## Como integrar o Git Local ao GitHub: (Comandos de clone, add, commit, push).


Para integrar o Git Local ao GitHub, o processo é simples e envolve alguns passos essenciais. Primeiro, você precisa criar um repositório no GitHub e copiar a URL fornecida na página do repositório. Com essa URL, você poderá conectar seu repositório local ao repositório remoto no GitHub.

No terminal, dentro do diretório do seu projeto, utilize o comando git remote add origin seguido da URL do repositório GitHub para vincular o repositório local ao remoto. Isso permitirá que você envie suas alterações para o GitHub.

Depois, adicione os arquivos que deseja versionar ao repositório local com o comando git add .. Isso coloca os arquivos na área de preparação (staging area). Em seguida, registre as alterações com um commit utilizando o comando git commit -m "Mensagem do commit", onde você descreve as mudanças feitas.

Por fim, para enviar suas alterações para o GitHub, utilize o comando git push -u origin main. Isso envia as mudanças da sua branch local para o repositório remoto no GitHub, conectando definitivamente o repositório local ao GitHub.

## Como adicionar colaboradores ao repositório privado

Para adicionar colaboradores a um repositório privado no GitHub, primeiro acesse a página do repositório e clique em Settings (Configurações) no menu superior. Em seguida, no menu lateral esquerdo, selecione Manage access (Gerenciar Acesso) e clique em Invite a collaborator (Convidar um colaborador). Digite o nome de usuário ou e-mail do colaborador no campo de busca, selecione o usuário desejado e clique em Add (Adicionar). O colaborador receberá um convite por e-mail e, após aceitá-lo, terá acesso ao repositório. Dessa forma, ele poderá colaborar com você no projeto privado.

## Como usar o GitFluence

O **GitFluence** é uma ferramenta gráfica que simplifica o uso do Git, permitindo gerenciar repositórios, fazer commits, criar branches e realizar merges sem precisar usar comandos no terminal. Com ele, você pode clonar repositórios, adicionar arquivos ao staging, visualizar o histórico de commits e fazer push/pull para repositórios remotos de forma intuitiva. Embora seja ideal para iniciantes ou para quem prefere uma interface visual, o GitFluence não substitui os comandos do Git para tarefas avançadas.
