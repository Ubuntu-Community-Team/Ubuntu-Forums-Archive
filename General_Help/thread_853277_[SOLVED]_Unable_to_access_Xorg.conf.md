---
title: "[SOLVED] Unable to access Xorg.conf?"
date: 2008-07-08
forum: General Help
---

### Post by Paul T. on 2008-07-08
Hi, I'm a complete noob to Ubuntu & Linux and stumped at first hurdle.
Trying to open Xorg.conf file to check graphics settings, but despite logging in as root user I'm denied permission? Get the following message:

dad@dad-desktop:~$ sudo su -
[sudo] password for dad: 
root@dad-desktop:~# /etc/X11/xorg.conf
-su: /etc/X11/xorg.conf: Permission denied
root@dad-desktop:~#

---

### Post by Elfy on 2008-07-08
Try using cat or gedit

```
cat /etc/X11/xorg.conf
```

to view it, to edit
```
gksudo gedit xorg.conf
```

If I wasn't sure what I was doing I would be inclined not to have a terminal at root though just in case :)

---

