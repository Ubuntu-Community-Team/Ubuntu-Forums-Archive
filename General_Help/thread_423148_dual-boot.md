---
title: "dual-boot?"
date: 2007-04-25
forum: General Help
---

### Post by skippermike on 2007-04-25
My house-mates motherboard blew so i've put his harddrive in my PC and swap drives as necessary - this is due to him having a problem with my lovely installation of Ubuntu and 'needs' his windows.

Is it possible to configure a dual-boot set-up with two drives already set up to boot individually, one Ubuntu, the other, windows?

If so, how?

Thanks

---

### Post by goodfella on 2007-04-25
It is possible to set up a dual boot with two drives.  One setup to boot ubuntu and the other setup to boot windows.  It is the configuration I have.  I figured it would be a good idea to seperate my windows and ubuntu onto different drives.  The windows drive boots straight into windows when it is the first boot device and the ubuntu drive boots into grub giving me the choice of booting either windows or ubuntu.  

To set this up is pretty easy.  You just have to set up the menu.lst file under /boot/grub/.  All you need to know is what drive and partition your windows installation is on.  I got help from the following forum and its subsequent links:

[Dual Boot]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by skippermike on 2007-04-25
You are a star, thank you :)

---

