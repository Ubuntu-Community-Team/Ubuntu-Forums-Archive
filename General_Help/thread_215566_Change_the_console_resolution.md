---
title: "Change the console resolution?"
date: 2006-07-14
forum: General Help
---

### Post by Daniel15 on 2006-07-14
Hi, 
 I recently set up a server using Ubuntu, and I absolutely love it! (I previously used Debian, so I find Ubuntu quite easy to use :))

I'm just having one problem: I recently bought a KVM switch, so I can use my keyboard and monitor to control the server. However, the default resolution of the console is 720x400, which looks horrible on an LCD screen (I have a BenQ FP71G+). Is there any way to change this resolution to something that looks better on an LCD screen?

Thanks,
 --Daniel15

EDIT: Oh yeah, there's no X server on this PC. Just a base Ubuntu server installation, with a LAMP setup, and AFP/Brute Force Detection installed

---

### Post by mlind on 2006-07-14
You can use different vga mode. Just append appropriate mode on /boot/grub/menu.lst **# defoptions** line

```

Color depth	640x480	800x600	1024x768	1280x1024
---------------------------------------------------------
256 (8bit)	769	771	773		775
32000 (15bit)	784	787	790		793
65000 (16bit)	785	788	791		794
16.7M (24bit)	786	789	792		795

```

---

### Post by thingy on 2006-07-14
I think this might help:

In the /boot/grub/menu.lst file you'll have a line which specifies the vga= kernel boot time parameter.

 	Code:
 	[LEFT]## e.g. defoptions=vga=791 resume=/dev/hda5[/LEFT]
 
 
Change the value to a higher/lower res/depth as you see fit:

Code:
 	[LEFT]                 640x480    800x600    1024x768       1280x1024
256 colors        768        771         773            775
32K colors        784        787         790            793
64K colors        785        788         791            794
16M colors        786        789         792            795[/LEFT]
 
 
You will have to rule "update-grub" once you modify the file!

---

### Post by HAARP on 2006-07-14
What are the default settings?
Is it possible to set a refresh frequency? 60Hz are hurting my eyes ;)

---

### Post by Daniel15 on 2006-07-14
mlind and thingy, thanks for that! I think I'm getting somewhere now :)

I tried to boot up after doing what you suggested, and got this message:
> 
You passed an undefined mode number. Press RETURN to see video modes available

[[IMG]http://img106.imageshack.us/img106/9646/pict00163be.th.jpg[/IMG]](http://img106.imageshack.us/my.php?image=pict00163be.jpg)
(sorry about the quality, it's quite a bad camera... Yes, I did take a photo of the screen :p)

So, what should I do?

EDIT: If it helps, according to phpSysInfo, the graphics card is a 'Matrox Graphics, Inc. MGA G200 AGP'.

---

### Post by dbw on 2006-07-15
thingy & mlind - what do the numbers after the word "colors" indicate?

---

### Post by mlind on 2006-07-16
> **dbw said:**
> thingy & mlind - what do the numbers after the word "colors" indicate?

It's explained on [vesafb.txt]("http://www.mat.univie.ac.at/~gerald/laptop/vesafb.txt")

---

### Post by Irony on 2006-07-16
The numbers after the colors are the vga settings for example vga=794 is 1280x1024 resolution with 64k of colors. See;

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10)

For example;

[PHP]title		Dapper hda3, 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash vga=0x31A
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot[/PHP]

I added this vga setting because without it I had no virtual terminals and no text boot up and shutdown.

---

### Post by dbw on 2006-08-22
Thanks folks - every bit of knowledge helps.

---

