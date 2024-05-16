# Utilizando iptables para Configurar Redirecionamento de Portas

## Objetivo do Projeto

1. Configurar regras de redirecionamento de tráfego do iptables de forma conveniente.
2. Atualizar automaticamente as regras de redirecionamento quando o endereço de resolução de domínio muda (adequado para domínios DDNS).

## Uso

```shell
# Se o VPS não conseguir acessar raw.githubusercontent.com, use este comando
bash <(curl -fsSL https://www.arloor.com/sh/iptablesUtils/natcfg.sh)
```
ou

```shell
bash <(curl -fsSL https://raw.githubusercontent.com/arloor/iptablesUtils/master/natcfg.sh)
```
A saída será:

```shell
#############################################################
# Usage: setup iptables nat rules for domain/ip             #
# Website:  http://www.arloor.com/                          #
# Author: ARLOOR <admin@arloor.com>                         #
# Github: https://github.com/arloor/iptablesUtils           #
#############################################################

O que você deseja fazer (digite um número)? Ctrl+C para sair do script
1) Adicionar regra de redirecionamento    3) Listar todas as regras de redirecionamento
2) Remover regra de redirecionamento      4) Ver configuração atual do iptables
#?
```
Digite um número entre 1 e 4 conforme necessário e siga as instruções.

## Desinstalação

```shell
wget --no-check-certificate -qO uninstall.sh https://raw.githubusercontent.com/arloor/iptablesUtils/master/dnat-uninstall.sh && bash uninstall.sh
```
## Verificar Logs

```shell
journalctl -exu dnat
```
## Backup e Importação/Exportação de Arquivos de Configuração

Os arquivos de configuração estão em:

```shell
/etc/dnat/conf

```

## Redirecionamento Trojan

Algumas pessoas dizem que não podem redirecionar o Trojan, mas isso geralmente é devido à configuração incorreta de certificados. A solução mais simples é não validar o certificado no cliente. A solução mais complexa envolve configurar corretamente o certificado e o domínio do servidor de trânsito.

Para iniciantes: não valide o certificado no cliente.

## Recomendações de Novo Projeto – Redirecionamento NAT com nftables
O sucessor do iptables, nftables, já está disponível como ferramenta de produção nas últimas versões do Debian e CentOS. Ele resolve muitos problemas do iptables e oferece novos recursos.

Assim, foi criado um novo projeto /arloor/nftables-nat-rust. Este projeto usa nftables para redirecionamento NAT, com as seguintes vantagens:

Suporte a redirecionamento de intervalo de portas.
Regras de redirecionamento em arquivos de configuração, permitindo backup e importação.
Mais moderno.
Portanto, é altamente recomendado usar /arloor/nftables-nat-rust. Não se preocupe, este projeto ainda pode ser usado de forma estável.

PS: Os dois projetos não são compatíveis. Ao mudar para o novo projeto, desinstale este projeto primeiro.


## Grupo no Telegram
https://t.me/popstary


