---
title: "Falha temporária resolvendo 'br.archive.ubuntu.com'"
date: 2016-11-02
forum: General Help
---

### Post by kevinhunter on 2016-11-02
Im new to Linux, 

I have updated my linux to the newest release,  16.04 LTS, but I think something went wrong during the upgrade, or I did something wrong, IDK! 
Anyways Im trying to update and Im getting the following error:

```
green@green-To-be-filled-by-O-E-M:/etc/apt/sources.list.d$ sudo apt-get update
[sudo] password for green: 
Atingido:1 http://repo.steampowered.com/steam precise InRelease
Err:2 http://br.archive.ubuntu.com/ubuntu xenial InRelease                     
  Falha temporária resolvendo 'br.archive.ubuntu.com'
Atingido:3 http://archive.canonical.com/ubuntu xenial InRelease                
Obter:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [94,5 kB]  
Err:5 http://br.archive.ubuntu.com/ubuntu xenial-updates InRelease             
  Falha temporária resolvendo 'br.archive.ubuntu.com'
Err:6 http://br.archive.ubuntu.com/ubuntu xenial-backports InRelease     
  Falha temporária resolvendo 'br.archive.ubuntu.com'
Baixados 94,5 kB em 1s (75,5 kB/s)                                
Lendo listas de pacotes... Pronto
W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Falha temporária resolvendo 'br.archive.ubuntu.com'
W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Falha temporária resolvendo 'br.archive.ubuntu.com'
W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Falha temporária resolvendo 'br.archive.ubuntu.com'
W: Falhou o download de alguns ficheiros de índice. Foram ignorados ou os antigos foram usados em seu lugar.
```

---

### Post by howefield on 2016-11-02
Try opening the Dash and search for Software & Updates application, load it up and from the Ubuntu Software tab change the *Download from* setting to *Main Server*.

Then try your update again.

---

