---
title: "Can't get widescreen resolution"
date: 2007-07-21
forum: General Help
---

### Post by srunni on 2007-07-21
Hi,

I'm trying to get Kubuntu Feisty to work with a ViewSonic N2750w monitor, which has a native resolution of 1280x720. I've tried adding "1280x720" to my X11 configuration file, but I still don't get anything higher than 1024x768 in the KDE System Settings. Does anyone know how to fix this?

Thanks in advance for the help!!

---

### Post by kevinlyfellow on 2007-07-21
What graphics card to you have?

---

### Post by srunni on 2007-07-21
My graphics card is an Intel GMA 950 onboard video card.

---

### Post by kevinlyfellow on 2007-07-22
Have you installed 915resolution?  
```
 sudo apt-get install 915resolution
```
This is a hack used to fix intel resolution problems.  

Alternatively, I think that you can install the new graphics driver from intel
```
sudo apt-get install xserver-xorg-video-intel
```
and then change your xorg.conf file to read "intel" instead of "i810" or whatever it may happen to be.

---

### Post by ramjet_1953 on 2007-07-22
There is a problem with the new Intel driver in that it crashes X, if you use an application that dynamically changes the screen resolution. Full screen games are an example.

You are probably better of sticking with 915resolution.

Here is a link for setting-up either driver:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Regards,
Roger :cool:

---

### Post by kevinlyfellow on 2007-07-22
> **ramjet_1953 said:**
> There is a problem with the new Intel driver in that it crashes X, if you use an application that dynamically changes the screen resolution. Full screen games are an example.


I haven't had a problem with it, in fact I never even heard of the bug.  But, it is admittedly experimental for feisty, so use at your own risk.

---

### Post by srunni on 2007-07-22
The 915resolution hack worked perfectly. Thanks a lot for the help!

---

### Post by srunni on 2007-07-25
Actually, there's a problem - when I restart, the changes are being lost. I have to run ```
915resolution 5c 1280 720
``` as root and then restart X. I tried editing /etc/default/915resolution like it said in the guide that rajmet linked, but that didn't help. So I tried making a shell script containing ```
#!/bin/sh
915resolution 5c 1280 720
``` and saving it in /etc/init.d as an executable shell script, but that didn't work either. When I switched to verbose mode on startup, I think there was a message about 915resolution, but I couldn't read the message before it scrolled up. I tried to log the boot messages in /var/log/boot as detailed at [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925) , but that didn't work either. If anyone can solve any of these problems, I would greatly appreciate it.

---

### Post by srunni on 2007-07-25
By the way, I tried installing the Intel driver earlier for another purpose and it didn't work.

---

