---
title: "HELP ME - sudo doesn't work - error message"
date: 2004-11-19
forum: General Help
---

### Post by filattiera on 2004-11-19
Good morning,

I have a big problem, for me.
Yeasterday, I have change the permission on /usr/sbin with the command
chown -R root /usr/sbin
from my user that is the administrator user.

Today, I don't have the access to usr/sbin so some programme doesn't start (as synaptic...).

I try to change permission, but nothing because I am logged as user and not as root.

I try to change log:
sudo passwd root

but this is the message:
Sorry, sudo must be setuid root

I try to log:
su -s root

but ubuntu asks me the password that I don't  know.

Please, help me, I want to have the permission on usr/sbin as user and not only as root.

Thanks.
Luca.

PS.
Also user and group menagement is not active as user (root user).


 ](*,)  ](*,)

---

### Post by b10m on 2004-11-19
Try to root login directly from tty and then change the permission in /usr/bin.
Sudo works with user permission and if you can't access to /usr/bin obviously you can't run it

---

### Post by filattiera on 2004-11-19
Thanks.

What is tty?
I think from the gdm console at the beginning image.

Ciao.
Luke

---

### Post by b10m on 2004-11-19
TTY is THE virtual terminal or console.
You can access it by ctrl+alt+f1 (or f2, f3....)

Bye

---

### Post by filattiera on 2004-11-19
[QUOTE=b10m]TTY is THE virtual terminal or console.
You can access it by ctrl+alt+f1 (or f2, f3....)

Bye[/QUOTE]

Thanks a lot.
Ciao.

Luke.

 :-)

---

