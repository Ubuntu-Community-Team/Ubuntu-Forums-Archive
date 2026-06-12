---
title: "X server Error, Does not load GDM"
date: 2007-05-06
forum: General Help
---

### Post by Warboy on 2007-05-06
Ok, I tried to update my drivers.

When i went to reboot, it rebooted then started to load normally. Then It says

"X Server can not load, Do you wish Diagnose" "No Desktop" "Please Repair X Server then Load GDM"
So how do i fix this? I'm really new to linux.

---

### Post by scrooge_74 on 2007-05-06
You probably have some problem with the video driver, which video card you have?

Try this: sudo dpkg-reconfigure xserver-xorg  then reply to the questions about video driver, if you are not sure which card you have use a VESA driver so at least you can have a basic desktop working

---

### Post by Warboy on 2007-05-06
I'm using a Nvidia 7950 GT, Also, That didn't work.

---

### Post by scrooge_74 on 2007-05-07
try it again but use the nvidia driver that comes standard with ubuntu, you wont have 3D but at least you can start over

Check this website

[http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

### Post by Warboy on 2007-05-07
I'm using 7.04 and I already tried re-installing the drivers via command propt because thats all i can have, i wish i could have a working desktop interface.

[[IMG]http://img182.imageshack.us/img182/4250/1000152ea6.th.jpg[/IMG]](http://img182.imageshack.us/my.php?image=1000152ea6.jpg)

[[IMG]http://img243.imageshack.us/img243/91/1000153er4.th.jpg[/IMG]](http://img243.imageshack.us/my.php?image=1000153er4.jpg)

there is what i get.

---

### Post by scrooge_74 on 2007-05-07
check in the /var/log the xserver error file to see what is wrong

once I had problems with a ps2 mouse which was not set properly

---

