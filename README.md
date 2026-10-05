# SIGIEM — aplicativo desktop

Sistema Integrado de Gestão de Igrejas e Membros.

Este repositório distribui os **instaladores públicos** e as atualizações do SIGIEM. O desenvolvimento do sistema ocorre em um repositório separado.

## Download

As versões publicadas ficam em [Releases](https://github.com/samuelr357/SIGIEM-App/releases).

| Sistema | Pacote | Instalação |
|---|---|---|
| Windows x64 | `SIGIEM-<versão>-win-x64.exe` | Executar o instalador; programa em `C:\SIGIEM` |
| Linux x86_64 | `SIGIEM-<versão>-linux-x86_64.run` | Executar `sh nome-do-pacote.run`, sem sudo; programa em `~/SIGIEM` |

Node e SQLite vêm incluídos. No Linux, o programa é extraído somente durante a instalação/atualização; o atalho abre diretamente o executável instalado. São necessários um ambiente gráfico, glibc e as bibliotecas do Electron. O instalador informa dependências ausentes.

Na primeira abertura, cadastre a igreja sede e o administrador. Ao fechar a janela, o servidor continua no ícone próximo ao relógio. Use o menu desse ícone para abrir a janela, reiniciar o servidor ou fechar o aplicativo.

## Atualizações

A versão 0.3.0 e posteriores consultam este repositório público automaticamente. **Não é necessário GitHub, conta ou token para quem instala.** Uma nova versão aparece no aviso e em **Sobre e atualizações → Atualizar agora**.

O download é verificado por SHA512 e o app cria uma cópia de recuperação antes de instalar. Banco, imagens e backups são preservados em `C:\SIGIEM\data` ou `~/SIGIEM/data`.

Quem usa uma instalação antiga deve instalar o 0.3.0 uma vez sobre ela, preservando a pasta de dados. No Linux, isso migra a instalação antiga de AppImage para o instalador .run.

## Publicação pelo mantenedor

1. No repositório de código `samuelr357/SIGIEM`, configure o Secret de Actions `SIGIEM_RELEASE_TOKEN`, com **Contents: Read and write somente neste SIGIEM-App**.
2. Envie o código para a branch `samuel` e crie nesse repositório uma release/tag estável, como `v0.3.0`, apontando para `samuel`.
3. O workflow **Publish desktop version** testa e gera Windows e Linux, envia os instaladores e metadados para este repositório e publica a release quando ambos estiverem completos.

O secret pertence somente ao workflow de publicação e não é incluído no app. Um push comum de código não publica versão. As novidades escritas na release de origem são tornadas públicas. Não reutilize tags; publique `v0.3.1`, `v0.3.2` etc.

Cada release completa contém `.exe`, `.run`, `latest.yml`, `latest-linux.yml` e `SIGIEM-update-ready.json`. Os metadados são enviados depois dos instaladores, para oferecer apenas downloads completos.

## Suporte

Relate problemas em [Issues](https://github.com/samuelr357/SIGIEM-App/issues), informando versão do aplicativo, sistema operacional e passos para reproduzir. Não inclua banco de dados, credenciais ou informações de membros.
