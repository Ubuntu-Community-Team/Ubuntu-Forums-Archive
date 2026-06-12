---
title: "How to have a file system accessible by all thin clients on a network...?"
date: 2008-03-14
forum: General Help
---

### Post by sajro on 2008-03-14
I am working on a lab setup (COMPLETE documentation will eventually be published for anyone looking to do similar). I need to have all my thin clients access the same RAID array for storage. There will be at least 80 clients connected at any one time so I need it to not kaput on me. Any suggestions?

---

### Post by dcstar on 2008-03-15
> **sajro said:**
> I am working on a lab setup (COMPLETE documentation will eventually be published for anyone looking to do similar). I need to have all my thin clients access the same RAID array for storage. There will be at least 80 clients connected at any one time so I need it to not kaput on me. Any suggestions?

Just install samba, and share the array as you would any other folder.

---

### Post by sajro on 2008-03-15
> **dcstar said:**
> Just install samba, and share the array as you would any other folder.

Not to seem ignorant, but ... Samba isn't jsut for Lin-to-Win?

---

### Post by fjgaude on 2008-03-15
> **sajro said:**
> Not to seem ignorant, but ... Samba isn't jsut for Lin-to-Win?

Samba works win to linux, linux to win, linux to linux, from my experience.

Make sure you enter the smbpasswd for each user that will have access to the array.

```
sudo smbpasswd -a name
```

You can setup Samba from the System/Administartion menu under Shares in Ubuntu.

---

### Post by HermanAB on 2008-03-15
Samba will work, but NFS is much easier to set up.

---

