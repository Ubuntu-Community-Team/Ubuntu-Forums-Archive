---
title: "Shared folder - set permissions automatically?"
date: 2008-04-03
forum: General Help
---

### Post by zoopzoop on 2008-04-03
I set up Samba to share a folder to a Windows machine and followed [this howto]("http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend").
Now I have a shared folder with the right permissions but everytime I copy something into it, I have to run chown and chmod again so enable write access from the Windows machine.
Is there a way to set up this folder so that certain permissions get applied to everything I copy into it automatically?

---

### Post by ryanhaigh on 2008-04-04
I think what you need to do is add a create mask and directory mask to your smb.conf for the shares. [http://codept.blogspot.com/2007/09/umask-creation-mask-in-samba.html](http://codept.blogspot.com/2007/09/umask-creation-mask-in-samba.html)
That page doesn't have much info but google will help.

---

