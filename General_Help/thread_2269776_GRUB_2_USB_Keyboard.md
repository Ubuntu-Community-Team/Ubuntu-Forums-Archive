---
title: "GRUB 2 USB Keyboard"
date: 2015-03-18
forum: General Help
---

### Post by geekyhawkes on 2015-03-18
Hello;

I have a dual boot Windows 7 / Xubuntu 14.10 with Grub 2 machine running on my laptop.  My keyboard on my laptop has died and Grub doesnt recognise my USB keyboard so I am not stuck with the default option and have lost my dual boot.

I have searched and tried lots of things but still have the issue:

BIOS: USB Legacy mode is enabled.  
Mouse Pointer:  Removed USB mouse pointer but the keyboard still ignored
Add usb usb keyboard to grub loaded modules, saved changes and updated grub - same issue.

Pre-Grub the USB keyboard works fine, Num Lock, Caps Lock and can even trigger the PC to enter the BIOS.  Once past GRUB loader screen again the keyboard works fine.  

Very occasionally if i press buttons on the USB keyboard pre Grub (so smashing CTRL or space etc) the keyboard is detected in GRUB, but its far from a certain thing and often ends in the same issue of the default OS being loaded.

Thanks for any help, this issue is killing me!

Andy

---

### Post by geekyhawkes on 2015-03-19
I have also tried disabling the internal pointing device in the bios but sadly that makes no difference either. Any help well received please!

---

### Post by dino99 on 2015-03-19
i'm not a xubuntu user, but i've seen lot of xubuntu packages been upgraded the past days. So it can be related with one of them. you can disable the 'proposed' archive, then reload the archive to get the list of 'proposed' packages. And finally picking these packages for downgrading

maybe you will find a buggy package

---

### Post by geekyhawkes on 2015-03-19
I am 100% its not related to the OS - the issue is GRUB I think.  I have tried multiboot with Ubuntu and Xubuntu and Windows Xp/7 and always get the same result.  GRUB2 doesnt see my USB keyboard.  I have googled a fair bit and its widespread, but no one seems to have a consistent solution.

---

### Post by tgalati4 on 2015-03-19
What prevents you from fixing the keyboard on your laptop?  Have you tried reseating the ribbon cable?  Was it soaked with a soft drink?

Perhaps boot with USB using SuperGrub and see if that has a keyboard driver.  Try different keyboards.  Somtimes an older, simpler keyboard may work.

---

### Post by geekyhawkes on 2015-03-19
So fixing the keyboard is sadly not an option as the cost from Samsung is lots!!! (its a backlit keyboard etc so the cost is high).  I have tried booting with a simple usb keyboard and get the same result - for interest I also tried the same on another laptop I have lieing around with the same results - Grub2 however I have set it doesnt like USB keyboards. 

Is it possible to roll back to Grub 1 without killing my setup?

---

### Post by geekyhawkes on 2015-03-22
I have tried installing burg today but have the same results. Does anyone have any ideas before I roll back to grub 1?

---

### Post by geekyhawkes on 2015-03-25
So I found a thread with similar issues and finally a solution: [http://ubuntuforums.org/showthread.php?t=2226621]("http://ubuntuforums.org/showthread.php?t=2226621")

as expected the issue lies with USB keyboard drivers with Grub 2 - revert back to Grub 1 and you are good to go!

---

