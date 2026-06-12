---
title: "Instalar o samba no Ubuntu 20.04"
date: 2021-03-26
forum: General Help
---

### Post by fagundessilva on 2021-03-26
Estou tentando acessar pastas compartilhadas de um servidor de dados em rede Windows. Mas não estou conseguindo tentei instalar o smb mas os comandos de instalação não estão funcionando. Alguém poderia me dar uma luz?

---

### Post by ActionParsnip on 2021-03-27
```
 
sudo apt-get install samba

```

If you could even use NFS instead if Samba is being a pain. Make sure your local firewalls allow suitable traffic

---

