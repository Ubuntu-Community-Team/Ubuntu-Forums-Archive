---
title: "Call fusemb automatically?"
date: 2007-03-21
forum: General Help
---

### Post by dv_ on 2007-03-21
Hi,
I use fusesmb for smb access. it is much more stable than smbfs, and works well here. However, I have to call "fusesmb /mnt/net" manually. Is there a way to invoke this command as my user at startup? Something like sudo username fusesmb /mnt/net maybe?

---

### Post by Ramses de Norre on 2007-03-21
You can put it in /etc/rc.local, it will then be ran just after the boot process with root priviliges.
Or you can put it in your ~/.bashrc, it will then be ran when you login with your user priviliges.

---

