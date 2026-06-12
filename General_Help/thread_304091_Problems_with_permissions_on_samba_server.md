---
title: "Problems with permissions on samba server"
date: 2006-11-21
forum: General Help
---

### Post by banexx on 2006-11-21
Hi there

I am having a problem with my samba server. I am trying to mount a samba folder when my computer boots and I have put the following into my fstab
```
//192.168.1.9/myshare /home/<username>/myshare cifs credentials=/root/.smbcredentials,uid=1000,umask=0777,iocharset=utf8 0 0
```
I am using cifs because I have read somewhere that in order to use danish letters I must use cifs instead of smbfs.

This all works fine except when I create a new file in /home/<username>/myshare, the filepermissions says 644 and I am now unable to edit the file.

Does anybody have an idea of how to fix this?

---

