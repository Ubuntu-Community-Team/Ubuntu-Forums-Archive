---
title: "adding DSL to grub"
date: 2007-05-12
forum: General Help
---

### Post by deadguy87 on 2007-05-12
I installed Damn Small Linux. Ubuntu and DSL are on the same HDD, of course difference partitions. I can't figure out how to put DSL into grub.

---

### Post by bernied on 2007-05-12
You need to create an entry in /boot/grub/menu.lst. Put it before or after the 'automagic' area, else it will get wiped on your next kernel upgrade.

It would look something like this:
```
title DSL
root (hdx,y)
kernel /boot/vmlinuz root=/dev/xdx# ro
initrd /boot/initrd
```
You would need to work out the values of x,y and xdx# before this will work - this will depend on how and where  you installed DSL

If you post your current menu.lst file and the output from:
```
sudo fdisk -l
```with perhaps a little interpretation (which partition is used for what?), then I'm sure someone here can help.

---

### Post by deadguy87 on 2007-05-13
the results for fdisk -l is this don't make fun of the tiny HD. this is my spare computer.
Ubuntu is on sda1 that's all I'm sure of 
Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1525    12249531   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda3   *        1526        2325     6426000   83  Linux

---

### Post by bernied on 2007-05-13
OK, so the entry would probably look like this:
```
title DSL
root (hd0,2)
kernel /boot/vmlinuz root=/dev/sda3 ro
initrd /boot/initrd
```
This should hopefully do it, the only thing is that I have guessed the names and locations of the kernel and initrd (initial ramdisk). Also your install may not be using a initrd, so that line might not be necessary. If this doesn't work, you should find the correct names and locations of those files and change them in the grub menu entry.
The [DSL wiki](http://www.damnsmalllinux.org/wiki/index.php/Installing_Grub) has lots of information, but I don't know what version you have, so can't guess any better than I already have.

---

### Post by Herman on 2007-05-13
When I used to have a DSL installation for a while, the name of the DSL kernel for it was 'linux24'.  They may have changed it though, it was some time ago when I had it.
In any case, I also remember that DSL had a lot of kernel options added to the boot entry too, although probably you could boot without them.
If it was me I'd just use a 'configfile' boot entry and let DSL boot up from its own menu.lst, like this,
```
title            Damn Small Linux, configfile boot on sda3
configfile    (hd0,2)/boot/grub/menu.lst
``` That would be a little simpler, and should work well.
Regards, Herman :)

---

### Post by john_spiral on 2007-05-13
Have you managed to get it to work? If so how are you finding it?

---

### Post by deadguy87 on 2007-05-18
I tried reformating the HD and my copy of DSL just doesn't want to run from the HD. I installed just DSL and it didn't want to boot. I'll find another light weight distro, and thanks for education of grub it will come in useful.

---

