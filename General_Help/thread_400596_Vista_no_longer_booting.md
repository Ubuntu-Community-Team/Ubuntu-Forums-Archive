---
title: "Vista no longer booting"
date: 2007-04-03
forum: General Help
---

### Post by ninocass on 2007-04-03
I have been able to dual boot my vista and ubuntu for weeks but just tonight its no longer working.

I havnt changed any partions the only thing i did was remove an old kernal image and run update-grub.

My set up looks like:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        3211    25784325    f  W95 Ext'd (LBA)
/dev/sda2   *        3212        5797    20772045   83  Linux
/dev/sda3            5798       14593    70653870    c  W95 FAT32 (LBA)
/dev/sda5               2        3211    25784293+   7  HPFS/NTFS

```

It seems that /dev/sda1 is the extended partion inside that is the /dev/sda5 which is my windows partition

inside my grub menu.lst i have:
```

title "Windows Vista"
root (hd0,0)
chainloader +1 

```

the above is giving me 
```

Grub Error 13: "Invalid or unsupported executable format"

```

im thinking that the root(hd0,0) is fecked up but its what grub is entering in automagically :)

helpy me pleaseeeeeeeeeeeeeee

thanks

nino

---

### Post by spankymasterc on 2007-04-03
ok try this open terminal and type sudo gedit /boot/grub/menu.lst enter password and scroll down where your vista is and do replace root to this

root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

then save and restart and try to boot....

---

### Post by ninocass on 2007-04-03
Thanks for the reply :)

now were getting a grub error 12

```

12 : Invalid device requested.

```

---

### Post by ninocass on 2007-04-04
nobody?

Im thinking should i nuke the MBR set it to windows so i can at least boot windows and then reinstall grub?

---

### Post by spankymasterc on 2007-04-04
try changing the 0,0 to 0 1 on root

u can reinstall grub from live cd 

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

if all fails reinstall the grub lol

---

### Post by ninocass on 2007-04-04
I ended nuking my vista install but then vista wouldnt reinstall as the NTFS partition wasnt active.  Ultimate Boot CD saved the day and the Fdisk tool allowed me to set the NTFS as active.  Reinstalled vista and used a live CD to reinstall grub as per these instructions:

[http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

and now everything is working a charm  :D

---

