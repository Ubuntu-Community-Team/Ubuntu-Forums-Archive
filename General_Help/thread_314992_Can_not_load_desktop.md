---
title: "Can not load desktop"
date: 2006-12-08
forum: General Help
---

### Post by lucid_dream on 2006-12-08
When booting into Edgy Eft Gnome freezes and will not load desktop. After I log in the splash screen freezes and will not finish loading. I can still switch between terminals but I can not get to my desktop. What can I do?

---

### Post by taurus on 2006-12-08
Log into a console and check the permissions of your $HOME directory...

```
ls -la ~
```

---

### Post by lucid_dream on 2006-12-08
Here is the output form ls -la

```
total 488
drwxr-xr-x  8 root root   4096 Dec  8 12:20 .
drwxr-xr-x 21 root root   4096 Dec  2 18:11 ..
-rw-------  1 root root     28 Dec  7 18:05 .bash_history
-rw-r--r--  1 root root   2227 Jun 30 09:03 .bashrc
-rw-r--r--  1 root root 446722 Dec  3 00:24 .fonts.cache-1
drwx------  2 root root   4096 Dec  4 12:53 .gconf
drwx------  2 root root   4096 Dec  4 12:53 .gconfd
drwx------  3 root root   4096 Dec  3 00:30 .gnome2
drwx------  2 root root   4096 Dec  3 00:30 .gnome2_private
-rw-r--r--  1 root root    141 Jun 30 09:03 .profile
drwx------  3 root root   4096 Dec  4 12:55 .synaptic
drwxr-xr-x  2 root root   4096 Oct 25 08:34 .wapi
-rw-r--r--  1 root root      0 Dec  8 12:20 file123

```

---

### Post by taurus on 2006-12-08
I mean you log in with your username and password, not as root!!!  But if your username is *lucid*, then run

```
ls -la /home/*lucid*
```

---

### Post by lucid_dream on 2006-12-08
I will have to get you the out put after wrok when i can get back to my linux box.

---

