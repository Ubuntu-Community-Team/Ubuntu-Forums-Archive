---
title: "i create a dir"
date: 2007-07-12
forum: General Help
---

### Post by Wuu on 2007-07-12
i create a dir 
[PHP]mkdir /home/sphere[/PHP]
and try to add new owner but can't :(
[PHP]chown main /home/sphere[/PHP]
and i can't delet it ....

wtf?

and how to log in with root in terminal?

---

### Post by McNils on 2007-07-12
To log in as root in a terminal you just type **sudo -i**.

---

### Post by davidjmayo on 2007-07-12
To use CHOWN you need to add some things about permissions.

Maybe you should read a bit more before you do things you may regret

---

### Post by Wuu on 2007-07-12
senx! :-\"

---

### Post by Meneldir on 2007-07-13
did you try with "rm -r /home/sphere"? in case you don't have permission, try with "sudo". "sudo rm -r /home/sphere"
be careful with what you try to remove with sudo... :P

---

