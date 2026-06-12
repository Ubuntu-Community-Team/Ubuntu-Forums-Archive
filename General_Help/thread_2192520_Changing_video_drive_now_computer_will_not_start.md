---
title: "Changing video drive now computer will not start"
date: 2013-12-08
forum: General Help
---

### Post by ronbrooks on 2013-12-08
Using Ubuntu 12.04 and I did the check for new drivers and I changed the drive I had to one of the ones that came up but now the computer will not get me to the log in screen instead I get the pannel log in screen.  After I log in I am looking at the terminal screen.  How can I get the old driver back that was working it is a Nvidia card in my HP lap top computer.

---

### Post by heir4c on 2013-12-08
Try first after login in the 'Console' (the pannel log in screen) to use the command: startx
If that not working, reboot and choose in the Grub-menu the recovery mode and when you see the menu you can choose there for failsafex (or something like that) or you just push Enter and then it will normally start to the desktop. If that happen then you can change it back to the old setting.

---

### Post by ronbrooks on 2013-12-08
I get this error Nvidia kernel module has version 304.88 but this nvidia driver component has version 173.14.35. How can I change it?

---

### Post by oldfred on 2013-12-08
It seems like you have mixed legacy nVida with current nVidia. But which is correct for your nVidia card/chip?

 What is a nVidia Legacy GPU?
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
 There are presently four Legacy GPU driver series. 

 GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. 
GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Probably best to purge all nVidia drivers and components and reinstall the correct one.
Some instructions on purging in posts by Bogan.

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by ronbrooks on 2013-12-08
Thanks old fred I got the nvidia card now to work but now it gets me to the sign in screen but when I enter my pass word and it just circle back to the log in screen. It is like something else is going on.  I am not sure what is going on now but I can't get pass the log in screen. 

Okay I just tried to log in as guest and it did log in on the lap top so I am guessing that there is something wrong with my log in settings.  Does anyone have any Idea as how to fix it.

---

