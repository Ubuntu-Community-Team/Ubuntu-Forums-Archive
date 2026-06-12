---
title: "Usplash on Ubuntu Server?"
date: 2007-04-24
forum: General Help
---

### Post by navilon on 2007-04-24
I have Ubuntu Server 7.04 and I would like to install a boot splash.

i have tried the following and it wont seem to work.
```
sudo aptitude install usplash usplash-theme-ubuntu
sudo dpkg-reconfigure usplash usplash-theme-ubuntu
```

Any suggestions?

---

### Post by qhartman on 2007-05-24
Do your kernel entries in your grub menu.lst file have "splash" in them? If not, that will need to be added. It's possible that simply running "sudo update-grub" may do what you need.

---

