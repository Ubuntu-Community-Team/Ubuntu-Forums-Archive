---
title: "Major Problem!!!"
date: 2007-10-28
forum: General Help
---

### Post by Heliodoros on 2007-10-28
(i wrote this topic while on the live-cd of Ubuntu 7.4)

Here is what i have:

hard drive 250GB
 partition 1=Windows XP
 partition 2=Windows Vista
 boot loader= GRUB Loader(the Ubuntu one)
USB hard drive 300GB ntfs formated

 Here's the story:
I had XP and Vista dual booting with no problems. I decided to install Ubuntu on the 300GB USB drive... and i did it... After some errors that i didn't like i decided to format the USB drive to uninstall Ubuntu. Ii did so. But when i tried to reboot the PC i had error with the GRUB loader which could not find the Ubuntu operating system. The xp/vista cd/dvd wont help...so don't count on doing fixboot command on recovery console...

Thats what i want to do:

-Fix the boot loader so it will start with the xp or vista (i don't care which of those it would be)... notice that i cant login into any of the 2 operating systems... Recovery console wont help me do anything.(vista dvd isn't working and the xp has broken recovery console)
-or tell me how to backup some files that i need in both XP and Vista partitions (ntfs)... Notice that i cant write any file to my USB drive because it is formated to fat32 or ntfs so i will be able to write and read files from the windows OS after backup...(lastest option... if i do that i will have to format the whole pc in order to install XP again and after that...vista)

The best i would prefer is to help me fix the boot sector so it will boot on XP or Vista...:(:(:(

---

### Post by ed-koala on 2007-10-28
Since no one has replied, I'll put in my 2 cents worth for ya.

Have you tried removing the 300gb drive entirely and booting the PC?  I assume so, but if not that may get you into windows, and from there format the 300gb drive again and see if that helps.

I'm no expert on this sort of problem, but I hope it helps.

---

### Post by Gas_Man on 2007-10-28
using the live cd open a terminal and use cfdisk to fix your bootable usb drive

```
sudo cfdisk /dev/sda1
```

or

```
sudo gparted
```

and you might try the boot from first hard disk option on the live cd menu.

you might also want to check you system bios to see which disk is the primary boot disk ... hd0 or usb or what ever you have set for the first boot device

---

### Post by Heliodoros on 2007-10-28
yes... but the problem is that.... i installed the ubuntu loader in hd0 by accident and i realised that after :P

---

### Post by Gas_Man on 2007-10-28
well in that case try:


```
sudo gedit /boot/grub/menu.lst
```

then fix the boot location pointer and then run 

```
sudo grub-install /dev/hda
```

warning ... you might want to use **man grub-install** and **man grub** first

---

### Post by Heliodoros on 2007-10-28
i managed to login into XP by making a bootable floopy that has a boot.ini and boots the XP loader... Now is there any way to reactivate the vista loader from XP?

---

### Post by larryfroot on 2007-10-28
If you have a boot disk of a windows persuasion using fdisk /mbr or  fdisk \ mbr (cant remember which flag is which) will overwrite grub and will restore a fully working windows master boot record. Hope this helps, although using the advice re grub here is as good a way as any... a boot loader is a boot loader, as long as it gets the job done.

---

### Post by Heliodoros on 2007-10-28
> **larryfroot said:**
> If you have a boot disk of a windows persuasion using fdisk /mbr or  fdisk \ mbr (cant remember which flag is which) will overwrite grub and will restore a fully working windows master boot record. Hope this helps, although using the advice re grub here is as good a way as any... a boot loader is a boot loader, as long as it gets the job done.

i dont have the vista disk.... and i want to enable the vista loader :P

---

### Post by Heliodoros on 2007-10-28
if the ubuntu community cant help me..... then who can? :P

---

