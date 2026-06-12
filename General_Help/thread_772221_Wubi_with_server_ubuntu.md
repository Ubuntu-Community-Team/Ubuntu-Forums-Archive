---
title: "Wubi with server ubuntu"
date: 2008-04-28
forum: General Help
---

### Post by exadeci on 2008-04-28
Hi,
I would like to install an server version of ubuntu on my computer and I would like to know if it would work because there are some things to configure for a server

---

### Post by ago on 2008-04-28
I would not recommend using Wubi for a server, it is ok for evaluation purposes. What you can do is run the wubi installer. Before rebooting edit C:\ubuntu\install\custom-installation\preseed.cfg and change "ubuntu-desktop" for "ubuntu-standard" ([https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)) and from there install the server packages as needed after installation.

---

### Post by exadeci on 2008-04-28
So I let wubi download the desktop version of ubuntu, and I change the cfg, and then when it's boot I can configure it ?


PS: Sorry for my bad english

---

### Post by ago on 2008-04-28
Yes. By installing ubuntu-standard you will not get a graphical user interface but you have apt

---

