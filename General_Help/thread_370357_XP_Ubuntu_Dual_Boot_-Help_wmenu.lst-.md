---
title: "XP Ubuntu Dual Boot -Help w/menu.lst-"
date: 2007-02-25
forum: General Help
---

### Post by xiqtem on 2007-02-25
I have done dual boot before with mepis and windoze.  I have xp installed on hda1.  I installed ubuntuCE on hda2 and the swap on hda4.  I need to know how to edit my menu.lst file to map it correctly.  I am not a newb, but I'm not as experienced with linux as I want to be. :)

---

### Post by brettg on 2007-02-25
You probably need to provide more info as to what problem you have.

nb. If you install XP and then follow that with an Ubuntu install, then the Ubuntu installer should automatically configure grub to load XP for you.

If that has not worked then you will need to describe the nature of your problem.

---

### Post by Maestro23 on 2007-02-25
Using the nano text editor:

> sudo nano -B /boot/grub/menu.lst

-B makes a backup of the file before editing.

*Before you do any of that, do what brettg posted above.

---

### Post by xiqtem on 2007-02-27
What info do you require in addition to what I provided before you can offer assistance?  I will be glad to provide you with it if I know what you need to know. :)

---

### Post by nyinge on 2007-02-27
As brettg pointed out, you can just install Ubuntu AFTER installing XP, and the installer will take care of the problem.  I don't think you will need to tweak the menu.lst configuration.

---

### Post by xiqtem on 2007-02-27
I installed xp first and ubuntu seccond and mepis last.  here is my drive partitions and menu.lst

my windows drive is /dev/hda1 it is a primary drive.  in qparted it shows as 01 ntfs.
i edited my menu.lst and got mepis and ubuntu to boot now all I have to do is get my windows to boot here is partitions

01 hda1 windows
hda2 extended 
hda3 fat32
07 hda4 swap
03 hda5 root
04 hda6 home
05 hda7 root
06 hda8 home

here is my menu.lst

timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at hda5, kernel 2.6.15-25-386
root 
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 nomce quiet vga=791 
boot

title Windows at hda1
rootnoverify (hd0,0)
chainloader +1

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title MEMTEST
kernel /boot/memtest86+.bin


any help would be appreciated.  thanks.

---

### Post by nyinge on 2007-02-27
I found a post on Mepis forum, and the guy had an exactly setup as yours.  Things look pretty much the same, except he doesn't have "savedefault" line in his menu.lst.  Here's [the post]("http://www.mepis.org/node/9203#comment-32360").

---

### Post by confused57 on 2007-02-27
Adding "makeactive" may help:

```
title Windows at hda1
rootnoverify (hd0,0)
makeactive
chainloader +1
```

---

