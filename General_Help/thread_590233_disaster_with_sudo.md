---
title: "disaster with sudo"
date: 2007-10-24
forum: General Help
---

### Post by LittleKoy on 2007-10-24
I was following a guide in order to install KDE4, and I had to modify a file using sudo visudo.
The guide told me to add %admin ALL = NOPASSWD: /usr/bin/make install at the end of file... Probably instead of "admin" I had to put my username :D 
But now everything I try to do the system tells me I haven't the permission... What can I do? Help me please .é.è.

---

### Post by taurus on 2007-10-24
Boot into recovery mode from GRUB menu and remove that line that you added in from /etc/sudoers.

```
nano -B /etc/sudoers
```
Save it with <Ctrl>o and exit with <Ctrl>x.  

Reboot

```
shutdown -r now
```
and see if you can sudo again.

```
sudo apt-get update
```

---

### Post by LittleKoy on 2007-10-24
It worked! The power is back *_*

Thank you very much :)

---

### Post by taurus on 2007-10-24
Glad to hear you got your Ubuntu back.  Just be careful when you edit /etc/sudoers next time.

---

