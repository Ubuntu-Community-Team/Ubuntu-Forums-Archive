---
title: "[SOLVED] How to enable 24bit color in Safe video mode ?"
date: 2008-06-12
forum: General Help
---

### Post by AJSB on 2008-06-12
Hello i'm new here :D

I have a problem with Ubuntu 8.04LTS...actually, it happens also with all derivatives like UE 1.8, MINT,etc....anything based in 8.04LTS.

Unless i boot in video safe mode, LCD  gets full of garbage....so i boot in Safe video mode where everything is OK....except that i found out that in safe mode the color palette is not in 24bit !!!!

That makes playing movies and DVD's real uggly !

I know that other Linux implementations of Safe mode (usually called VESA mode on them) let me yet choose color deep and i can use the 24bit color deep....but not in Ubvuntu !!!...or at least i haven't found a way ! :(


Is there a way to enable 24bit color deep in Safe Video Mode on Ubuntu 8.04LTS ?!?

TIA,
AJSB

---

### Post by komputes on 2008-06-12
What kind of video vard do you have, can you run the following command in a terminal and post the output:

$ lspci | grep VGA

---

### Post by AJSB on 2008-06-12
> **komputes said:**
> What kind of video vard do you have, can you run the following command in a terminal and post the output:

$ lspci | grep VGA

Yesi can...here is the result of the command:
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)

TIA,
AJSB

---

### Post by komputes on 2008-06-12
I think this should be using the via drivers then, if it's not you will need to manually write your xorg.conf file. Hardy automatically configures xorg (the local video server) at every reboot, I would try (I don't think it will work) but try booting into recovery mode from the GRUB prompt at boot (look for GRUB in the top left cornet and press ESC to get the menu, then select recovery).

Also if you want to check what driver is being used by automatic bulletproof x please upload the following log:

/var/log/Xorg.0.log

There are also people who are experiencing the same issue as you, so perhaps opening a bug on launchpad would be the best thing to do:
[https://answers.edge.launchpad.net/ubuntu/+question/11807](https://answers.edge.launchpad.net/ubuntu/+question/11807)

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...postnot relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...postnot relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...postnot relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...postnot relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...post not relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...post not relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...post not relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...post not relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...post not relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...post not relevant...

---

### Post by AJSB on 2008-06-12
"Erased" (how can we trully erase a message ?!?...post not relevant...

---

### Post by AJSB on 2008-06-12
PS: This Xorg log file was generated with the 8.04LTS DVD working as a LiveDVD booting in Safe Video Mode.
    However i don't think that differs in any relevant point from a boot from a HD with updated packages because i done that and problem was the same....this issue is common to Ubuntu 8.04, Kubuntu, Ultimate Edition 1.8 (based in U8.4LTS), Mint,et,etc....in all of them i have to boot in safe mode and in all of them it boots from CD/DVD/HD in 16bit color deep mode...and there isn't a "widget" (sp?) that i can use after boot to change color deep like in other distros that let me aFTER 1ST BOOT, CHANGE TO 24BIT....

Notice that , i'm a Linux newbie and only took a look to this for a minute, but it seems that only scans for 8,16 and 32 bit color deep modes and not 24 bit color deep....maybe that's the flaw ?
 
AFAIK, my board doesn't support 32bit but only up to 24bit....

Also, Ubuntu uses 16bit by default as you might notice...

TIA,
AJSB

---

### Post by AJSB on 2008-06-13
Great news for others with same problem than me :)
With the hints that i got here and my own findings, i figured out how to get 24bit color by default in 8.04LTS (actually in all variants of 8.04LTS like UE1.8, Mint) with a VIA card :)

Soon will post here details....need to go work in 2 hours...6:40AM here  :o 

I still want to tweak it a bit more....maybe access more screen resolutions but as is, it's already great :)
(Just for the sake of it, I want to access screen res 720x576 no matter i can go up to 1280x1024 in 24bit already....)

also, i want to test also Kubuntu which, of course,  also suffers from same problem.

AJSB

---

### Post by AJSB on 2008-06-24
OK, here is how it's done....it might be edited if i can improve it...
It works with Ubunt, Kubuntu, Xubuntu; Linux Mint, ultimate Edition,etc,etc....anything that it's based in Ubuntu....for Debian 5.0 it's a bit more complex and different but i found it by myself also :D


1- Insert installation DVD.
2- When language choosing window pop's choose language right away (you CAN'T ALLOW thAt the timer runs out and boot goes on)
3- Press F3 for choose keyboard map ( not important for the video issue but a good idea anyway)
4-REALLY IMPORTANT: Press F4 and choose "Safe Video Mode" or similar named option !!!!
5- Proceed with instalattion or with a test ride with your flavour of Ubuntu...if you make the test ride,you notice that video is now working perfectly except not yet in 24bit mode...don't worry and install it or reboot and repeat previous steps to install.
6- After installation and rebooting, open a console and write if you nhave gedit and use a ubuntu based distro with gnome: 
   **gksudo** gedit /etc/X11/xorg.conf 
    (or if you don't have gedit installed try to replace gedit by nano this way: **sudo** nano /etc/X11/xorg.conf)
7-after introducing your pw, gedit or nano opens xorg.conf....go to section  secreen and write:
   DefaultDepth 24


the sectipon will look something like this after editing it:
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth 24
EndSection

   In gedit make Ctrl+S to save it, in nano make Ctrl+X, then press "Y" and finally press the Return key to save it.

   That's it !!!

From now on you have no more garbage in the screen AND have 24bit color depth activated for enjoying those movies :D

AJSB

---

### Post by joni b on 2008-06-25
Thanks.
I tried the above lines , but it didnt work at all. I think its the wrong command for Kubuntu8.04

---

### Post by AJSB on 2008-06-25
> **joni b said:**
> Thanks.
I tried the above lines , but it didnt work at all. I think its the wrong command for Kubuntu8.04

I just done it and works with Kubuntu 8.04 !!!


Remember, use sudo nano /etc/X11/xorg.conf

As for booting, you must boot from instalation DVD and use the sequence that i describe before start to install or use Kubuntu in live mode...

When booting in safe mode, Kubuntu/Ubuntu/Xubuntu/UE/Mint/etc. will boot with "vesa" driver and if then you install , it automaticlly make a xorg.conf file pointing to that driver and the driver line in xorg.conf will be with following text:

Driver "vesa"

If it's not with that text, modify it to read that way.
Driver line should be in the Device Section.


Regards,
AJSB

---

### Post by joni b on 2008-06-25
Hi,


When I type sudo nano/etc/X11/xorg.conf in the console termimal in comes up with a " command not found message" 


I installed Kubuntu8  with the safe graphics, but still cant change to 24bit color beacuse of these error messages.

---

### Post by joni b on 2008-06-25
Thanks again

I just managed to get into the terminal and edit it after trying.But just one more question to make sure I got this right: is the entry  meant to be  - DefaultDepth 24   or DefaultDepth  "24"    ?

---

### Post by AJSB on 2008-06-26
1- It's:  

  sudo nano /etc/X11/xorg.conf

  and not

  sudo nano/etc/x11/xorg.conf

  You removed the space between "nano" and "/etc..." , that's why didn't worked !!!


2- It's: 

  DefaultDepth 24

  In this parameter you can't use "".


Regards,
AJSB

---

### Post by AJSB on 2008-06-30
PS:

I downloaded the last verison of the openchrome driver source code at openchrome.org, compiled it and installed it..

It all went well and the video quality is EXCELENT....funny thing is that in xorg.conf there is no more need for DefaultDepth 24 line....it was enabled in 24bit right away.

Of course that you still to make installation in safe mode from DVD and after compilation and instalation of the 0.2.902 version of openchrome, you still need to edit xorg.conf to replace "vesa" by "openchrome".


AJSB

---

