---
title: "Using terminal to manipulate files on a remote windows share?"
date: 2007-05-01
forum: General Help
---

### Post by Jurio on 2007-05-01
Is it possible to create/move/delete/etc files to a remote windows server using the terminal window?

I tried using smb://domain%3Buser@server/e%24/ but the terminal command doesn't seem to like that.

Thanks :KS

---

### Post by disposable on 2007-05-02
Try smbclient:

[http://us1.samba.org/samba/docs/man/manpages-3/smbclient.1.html](http://us1.samba.org/samba/docs/man/manpages-3/smbclient.1.html)

---

### Post by jfinkels on 2007-05-02
> **Jurio said:**
> Is it possible to create/move/delete/etc files to a remote windows server using the terminal window?

I tried using smb://domain%3Buser@server/e%24/ but the terminal command doesn't seem to like that.

Thanks :KS

You may be looking for ssh...If you can manage to install an ssh server on the Windows machine, just type in the terminal:```
ssh admin@192.168.1.2
```
replacing admin with a user name and 192.168.1.2 with the computer's actual IP address.

---

