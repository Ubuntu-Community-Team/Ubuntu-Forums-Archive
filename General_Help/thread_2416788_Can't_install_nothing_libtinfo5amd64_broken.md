---
title: "Can't install nothing libtinfo5:amd64 broken"
date: 2019-04-15
forum: General Help
---

### Post by victorsoares on 2019-04-15
Hi everyone, I recently suffered a power shortage on one of my servers, and after that I cannot install or upgrade anything. When I try to do so this is the error I get:

```
Depois desta operação, 1.232 kB adicionais de espaço em disco serão usados.Você quer continuar? [S/n] S
Extraindo templates dos pacotes: 100%
Pré-configurando pacotes ...
dpkg: aviso: falta ficheiro de lista de ficheiros 'libtinfo5:amd64'; assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: erro fatal irrecuperável, a abortar:
impossível abrir arquivo com lista de arquivos do pacote 'mutter': Mensagem inválida
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

```
After this operation, additional 1,232 kB of disk space will be used. Do you want to continue? [S / n] S
Extracting templates from packages: 100%
Preconfiguring Packages ...
dpkg: warning: missing file list file 'libtinfo5: amd64'; assuming that the package does not currently have files installed
dpkg: irrecoverable fatal error, aborting:
unable to open file with mutter package file list: Invalid message
E: Sub-process / usr / bin / dpkg returned an error code (2)


```


What can be done with this. I have a MySQL database that I need to upgrade and because of it I'm stuck.

---

### Post by joegry on 2019-04-20
It looks like your package file list may have been corrupted.  Try reinstalling that package with the following command   sudo apt-get install --reinstall libtinfo5

---

