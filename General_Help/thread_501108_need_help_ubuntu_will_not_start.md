---
title: "need help ubuntu will not start"
date: 2007-07-14
forum: General Help
---

### Post by punkrockermike21 on 2007-07-14
i just installed ubuntu 7.4 on my comp. when i boot it up it loads fine but as soon as it gets to the login screen my monitor says i lost signal. it did the same thing when i tried to install it with the live cd. please help i am very new to this and i know it is something stupid

---

### Post by taurus on 2007-07-14
What's the spec of your machine, especially the video card and monitor?  

Try booting into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default and pick **vesa** as a driver for your graphic card for now.  You can install a driver for it later when you get up and running first.

When done, reboot with

```
shutdown -r now
```

---

### Post by punkrockermike21 on 2007-07-14
ok when i do that it says that xserve-xorg is not installed. thanks for the help

---

### Post by taurus on 2007-07-14
Same topic, [http://ubuntuforums.org/showthread.php?t=501089](http://ubuntuforums.org/showthread.php?t=501089)!  :roll:

---

