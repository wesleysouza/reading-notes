# Capítulo 3 - Utilizando o Shell

## Escolhendo o seu shell

Verificando o nome do usuário e depois o shell:
```shell
$ whoami
user
```

Verficando definição de conta de usuário no arquivo **/etc/password**:

```shell
$ grep user /etc/passwd
user:x:1000:1000:user,,,:/home/user:/bin/bash
```
Observe que no último campo é possível identificar que o shell é o bash que está como padrão no sistema.

Para saber mais informações do shell utilize o man, ele fornece a documentação para os comandos, formatos de arquivos e outros componentes do linux. Executando o man para o shell:

```shell
$ man bash
```
Para executar um shell diferente basta digitar o nome do shell (ex.: ksh, tcsh, sh, dash e etc):

```shell
$ sh
```

Para sair basta digitar o comando exit.

## Executando Comandos

Para executar um comando basta digitar ele no shell:

```shell
$ date 
# exibe a data
```

Outros comandos:

```shell
$ pwd
# imprime nome do diretório de trabalho atual
```

```shell
$ hostname
# imprime o nome do computador
```

```shell
$ ls
# imprime o nome das pastas e arquivos do diretório atual
```

Além do comando, é possível adicionar opções e argumentos para modificar o seu comportamento.

### Entendendo a sintaxe de um comando

#### Opções

As opções são adicionadas por meio de uma letra precedida de um hífem. Os dois comandos abaixo são equivalentes:

```shell
$ ls -l -a -t
$ ls -lat
```

Em ambos os casos, o comando ls é executado com as opções -l (listagem longa) -a (exibe os arquivos de ponto ocultos) e -t (lista por tempo).

Alguns comando incluem opções que são representadas por uma palavra inteira. Nesse caso, usa-se um hífem duplo (--). Por exemplo:

```shell
$ command --help
```
Sem o hífem duplo (--) as letras da opção help serão entendidas como palavras separadas.

Obs.: Podem existir comandos que não excessão a essa regra.

Nota: Você pode usar a opção --help como a maioria dos comandos para ver as opções e argumentos que eles suportam: por exemplo, experimente digitar:

```shell
$ hostname --help
```

#### Argumentos

Muitos comandos aceitam argumentos, eles podem ser o nome de um arquivo, diretório, nome de usuário, dispositivo ou outro item que informa ao comando o objeto sobre o qual ele deve atuar. Por exemplo:

```shell
$ cat /etc/passwd
```
Exibe o conteúdo do arquivo /etc/passwd em sua tela. Nesse caso, /etc/passwd é o argumento.

Em alguns casos os argumentos estão associados a uma opção. Desse modo, o argumento deve ser imediatamente seguido da opção, com duas diferenças:
1. Com opções de uma única letra, o argumento geralmente vem depois de um espaço;
2. Para opções de uma palavra, o argumento muitas vezes vem depois de um sinal de igual (=).

Exemplos:

```shell
$ ls hide=Desktop
# Exibe todos os diretórios e arquivos da pasta atual exceto o diretório Desktop
```

```shell
$ tar -cvf backup.tar /home/user
```

Nesse segundo exemplo, as opções instruem o comando a criar (c) um arquivo (f) chamado backup.tar que incluí todo o conteúdo do diretório /home/user e seus subdiretórios e exibe mensagens verbosas (v) conforme o beckup é feito. Como backup.tar é um argumento para a opção f, backup.tar deve vir imediatamente após a opção.

Outros Exemplos:

```shell
$ ls
$ ls -a
# Mostra todos os arquivos e diretórios da pasta atual, incluíndo os ocultos.
```

```shell
$ uname 
# Exibe o tipo do seu sistema.
$ uname -a
# Exibe o tipo do sistema, hostname, a compilação e a versão do kernel.
```

##### Informações de Identidade

Para obter informações de identidade digite o comando id no seu shell.

```shell
$ id
uid=501(user) gid=501(user) groups=105(sales), 7(lp)
```

Nesse exemplo:
- O nome do usuário é user;
- O grupo primário de user também se chama user, seu ID de grupo (gid) é 501;
- O usuário user também pertence a outros grupos, como: sales, lp e etc;
- Esses nomes e números representam as permissões que o chris tem para acessar os recursos do computador.

##### Informações sobre a sessão atual

Para obter essas informações utilize o comando who. Exemplo:

```shell
$ who -uH
NAME  LINE  TIME          IDLE  PID   COMMENT
user  tty1  Jan 13 20:57  .     2013  
```

A saída desse comando who mostra que:
- O usuário user está logado no tty1 (que é o primeiro console virtual conectado ao computador) e a sua sessão de login começou às 20:57 am 13 de janeiro; 
- O tempo IDLE mostra quanto tempo o shell ficou aberto sem qualquer comando ser digitado (o ponto indica que ele está sendo utilizando no momento); 
- O PID mostra o ID do processo do shell de login do usuário; 
- O COMMENT iria mostra o nome do outro computador da rede, ou o nome do display X local se o usuário estivesse usando alguma janela de terminal (por exemplo 0.0).





