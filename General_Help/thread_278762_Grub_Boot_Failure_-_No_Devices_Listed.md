---
title: "Grub Boot Failure - No Devices Listed"
date: 2006-10-16
forum: General Help
---

### Post by Berto on 2006-10-16
Hi, today I ruined my Grub installation, and I cannot figure out how to restore it.  If anyone could please help, I'd much appreciate it.

1.  When I boot with no CD in, my machine freezes before a Grub menu comes up

2.  When I boot from the Live CD, and choose "Boot from Hard Disk", there are no devices shown (there used to be, but I installed grub2 on the machine and now it doesn't work).

So I can only get in with the Live CD, and would like to use it to reformat my MBR and re-detect my partitions if at all possible.

My setup:
/dev/sda1 - Some FAT16 drive that's 8 clusters big
/dev/sda2 - Windows XP
/dev/sda3 - 1 GB linux swap
/dev/sda4 - Ubuntu

Could anyone help me with one/all of the following?:

a.)  Help me format the MBR and get me to boot off of /dev/sda4 /boot/initrd.img-2.6.15-27-386

b.)  Help me configure this grub2 setup that's on the hard drive right now so that I can get back into the machine and then reinstall grub or lilo

c.)  Help me just get into /dev/sda2 Windows Partition (I don't have a floppy drive to fdisk /MBR)

d.)  Somehow install grub (the default version) into /dev/sda4 so that the Live CD can see my /dev/sda4 /boot/grub/menu.lst and then I can blast away from there

e.)  Show me how to manually use the grub console commands from a blank grub screen to boot into /dev/sda4 one time and then blast everything away

Thank you for your time(!!), I'm a bit stuck right now.
berto

---

### Post by Berto on 2006-10-16
Fixed!

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub)

That saved me right there.  If I would have known about setup (hd0) I would have been fine.  I used to use Mandriva so I was always into Lilo.

Now back to getting Windows to be my default (yeah sorry but this is a work laptop, only 5% of my sales require linux)... I'm sure I'll mess it all up again!  ;)

---

