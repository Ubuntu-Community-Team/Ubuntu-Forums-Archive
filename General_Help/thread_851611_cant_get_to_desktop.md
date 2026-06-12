---
title: "cant get to desktop"
date: 2008-07-06
forum: General Help
---

### Post by kaos13 on 2008-07-06
Cant get into desktop. I tried to install the Oss sound driver to get X-FI card to work. it conflicted with the libflashsupport so i uninstalled it. oss installed so i rebooted the computer and it goes to command line. i uninstalled xserver and reinstalled it that did not work. 

Running Hardy

---

### Post by iaculallad on 2008-07-06
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by kaos13 on 2008-07-06
Thanks. it worked

---

### Post by bikerdave on 2008-07-07
Fixed my problem too, when I would boot up...all I would get is my background.

---

### Post by LaPeche on 2010-06-08
Hi, are these commands the same with Xubuntu 10.04 (alternate CD) ?

Regards.

---

