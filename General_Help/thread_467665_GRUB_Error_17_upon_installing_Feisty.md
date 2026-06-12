---
title: "GRUB Error 17 upon installing Feisty"
date: 2007-06-07
forum: General Help
---

### Post by JooSpocks on 2007-06-07
So....
           I have installed x86 Feisty on a Seagate external USB hdd. Here is my problem. To be honest, I'm not really sure where I need to put the bootloader (In the installation options, by default it's hd0, so after messing around a little, I decided it might be hd1 for the USB drive, as there are no other drives connected to my computer.) The filesystem is ext2, and GRUB is getting Error 17, because it can't mount the volume. It is trying to boot hd1,1. When I tell it to boot hd1,0 it says that it cant find the file (the linux kernel), and hd1,2 does not exist.

           So if you could tell me how to find out if I need to install GRUB on hd1, or sda, or whatever it may be, OR if you could help me get linux to boot without reinstalling Ubuntu and GRUB, it would be greatly appreciated. If you would like to know anything else about my system, I can provide you with any details that may be relevant.

Thanks for your time.

---

### Post by confused57 on 2007-06-08
If you're able to boot first to your external drive and you're getting a grub boot menu, highlight your Ubuntu entry, press "e" & change root from (hd1,x) to (hd0,x), then press "b" to boot...this change is temporary, but you can determine if it'll work.

---

### Post by JooSpocks on 2007-06-08
I was able to get feisty to boot by telling grub to boot off of hd0,1
I was wondering if there is a way to make it so that I don't have to change hd1,1 to hd0,1 every time I want to boot ubuntu.

Thanks for the help confused

---

### Post by confused57 on 2007-06-08
> **JooSpocks said:**
> I was able to get feisty to boot by telling grub to boot off of hd0,1
I was wondering if there is a way to make it so that I don't have to change hd1,1 to hd0,1 every time I want to boot ubuntu.

Thanks for the help confused

You can make the changes permanent in your menu.lst, open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

change your root to (hd0,1) in all your kernel entries and change the groot line also:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

Once you make the changes, quit & save...

---

