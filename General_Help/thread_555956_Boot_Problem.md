---
title: "Boot Problem"
date: 2007-09-20
forum: General Help
---

### Post by n8dude on 2007-09-20
I  recently bought a external hard drive and i had a bright idea (or at least i thought it was) to install ubuntu on it and use it in any computer i wanted to, so i use my existing ubuntu machine to install ubuntu on the external hd, and all goes well until i reboot my system. It thinks that the external hd is internal so it gives me a grub menu to boot from but if i dont have my hd plugged in then i get "error 21" is there any way to undo this at all without nuking my ubuntu install? You input and help is appreciated.:confused:

---

### Post by arkara on 2007-09-20
the problem is that you installed grub what you can do is to put your windows cd in and from the  recovery console
type : fixmbr

this will fix your master boot record and you will boot to windows nomaly
now plug in the ext hd and boot to windows
go to my comp and right click it from there try to insert ubuntu to the windows boot loader
this will may solve your prblem

---

### Post by n8dude on 2007-09-20
except for one problem though, that machine doesn't have windows, its straight ubuntu :) but what would i do from the terminal to fix it?

---

### Post by Tyke91 on 2007-09-20
so you have ubuntu on your computer and another ubuntu on your external drive?

i think your best bet is to not install grub, instead edit your mbr to boot from a usb drive first, if there isnt one, then to boot from a cd, and then a hard drive. this will only work if your external hard drive is usb (i've never used one, so i don't know). you should be able to control the boot process by unplugging the hard drive when you need to switch to a "normal" boot.

---

### Post by n8dude on 2007-09-20
I might not have explained it clearly, so i'll give it another go. :confused: I tried installing ubuntu on the ext. hd for personal use (carrying it around to other comps for my own desktop anywhere) but in the process of installing ubuntu on my ext. hd  it made my comp think now its doing a dual boot between the ext. hd and the internal hd so if I don't have the ext. hd plugged in, I can't boot into the one on my internal hd. I am really lost on how to fix this :( 
edit: oh btw it shows me a grub boot menu when the ext. hd is plugged in, but when it's not plugged in and i try to start the machine it says "error 21" when its loading the grub bootloader.

---

### Post by logos34 on 2007-09-20
> **n8dude said:**
> except for one problem though, that machine doesn't have windows, its straight ubuntu :) but what would i do from the terminal to fix it?

Use your Sabayon or ubuntu live cd to reinstall grub to both MBRs (internal and external disks), with each pointing to their respective boot directories.  Then add an ubuntu entry to your sabayon menu.lst (or grub.cfg or whatever it's called) so you can boot ubuntu from there when it's plugged in.  Installing grub to the USB drive means you can also boot it from any machine.

for ubuntu on the USB drive:
[B]
sudo grub 
find /boot/grub/stage1[/B]
(it will show two--use 'hd1,x' in next command, where x=root partition #)
[B]root (hd1,x) 
setup (hd1)[/B] --> writes grub to USB mbr
**quit**

To do the same for the internal disk, use 'root (hd0,x)'  and 'setup (hd0)'

---

### Post by n8dude on 2007-09-20
Thank you so much! That did the trick! :)

---

### Post by logos34 on 2007-09-20
You might also consider using the ['configfile' format ]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile")for your ubuntu entry in the sabayon menu.lst.  That way if you upgrade the ubuntu kernel (or do a dist upgrade to gutsy) you won't have to change it.

---

### Post by n8dude on 2007-09-20
But now I have another problem, I decided to scratch the idea of any-where ubuntu, so i went and gparted and slapped the disk back into one fat32 file system, and everything works fine in linux recognized the disk ok.... but then i plug it into my dad's lappy (windows) and it won't recognize it :( I then try mac osx, and still nothing got any idea about that and how i could fix this?

---

### Post by arkara on 2007-09-21
try to reformat the disk again to fat 32. always make sure that the disk is pluged in correctly and external power also..
and also unplug the disk carefully using the eject from linux and stop usb device from windows..
send back some feedback about your problem

---

### Post by n8dude on 2007-09-24
sorry its taking me so long to respond i have a lot of HW to do, (stupid math n' chem)
i should be doing something in the next few days.

---

