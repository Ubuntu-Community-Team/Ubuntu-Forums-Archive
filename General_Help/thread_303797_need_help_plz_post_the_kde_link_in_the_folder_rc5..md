---
title: "need help: plz post the kde link in the folder rc5.d"
date: 2006-11-20
forum: General Help
---

### Post by ghepardo on 2006-11-20
playing with kde autostart,runlevels and rcconf I deleted the link to kde from every rcn.d folder, so I am no more able to autostart X.

Can plz someone post the file here so I can restore that!?

I use edgy.

Thanks.

---

### Post by ghepardo on 2006-11-20
UP plz

---

### Post by scxtt on 2006-11-20
#:> **ll /etc/rc5.d/S99kdm**
lrwxrwxrwx 1 root root 13 2006-08-17 02:23 /etc/rc5.d/S99kdm -> ../init.d/kdm

command:

**sudo ln -s /etc/init.d/kdm /etc/rc5.d/S99kdm**

---

### Post by ghepardo on 2006-11-21
Thank you, but that file isn't just a link, is a shell script file also, so you should post me the content of the file (like open it with kate) and then I have to create the file, paste the content and then make it a link with ln -s.

Plz help me!

---

### Post by ghepardo on 2006-11-21
ok I solved the problem, I post the solution for future users:
u have to create the link file in all the rcn.d directory but rc1.d, so u have to do this command:

sudo ln -s ../init.d/kdm /etc/rc5.d/S99kdm
sudo ln -s ../init.d/kdm /etc/rc4.d/S99kdm
sudo ln -s ../init.d/kdm /etc/rc6.d/S99kdm
sudo ln -s ../init.d/kdm /etc/rc3.d/S99kdm
sudo ln -s ../init.d/kdm /etc/rc2.d/S99kdm

and it will work again.

---

