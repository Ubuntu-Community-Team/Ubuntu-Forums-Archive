---
title: "My XP is missing in grub menu"
date: 2008-02-13
forum: General Help
---

### Post by xoshnow on 2008-02-13
I had them both working fine in a single  partitioned hard drive, recently I turned  my pc on
as usual try to select the OS of choice, but xp home vanished and no where to be found, Please advice how to find XP again in the grub menu, I tried to add it manually  but gives me error 11. thanx in advance for any advice.

---

### Post by TheBoat on 2008-02-13
Do you have an entry for XP in /boot/grub/menu.lst?

---

### Post by xoshnow on 2008-02-13
No and I am sure did not delete any thing 


## ## End Default Options ##





title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ac2e1f53-d583-4201-a2c1-ba9df08c0daf ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ac2e1f53-d583-4201-a2c1-ba9df08c0daf ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS

---

### Post by TheBoat on 2008-02-13
Try adding this to the file.  > title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1If you had an update recently, menu.lst probably was updated too and you lost your windows entry.  If you add Windows under where it says AUTOMAGIC, then it won't get erased on an update.

---

### Post by xoshnow on 2008-02-13
Do I have a chance to add it again if so please how can i?

---

### Post by TheBoat on 2008-02-13
```
cd /boot/grub
```
make a backup
```
sudo cp menu.lst menu.lst_bak
```
insert the lines into the file with an editor (gedit in code)
```
sudo gedit menu.lst
```
and then save it

---

### Post by xoshnow on 2008-02-13
Thanx......... the Boat I am one step away, I did get to the xp loading , but it was the recovery partition for HP that is the factory installed. that is what I added at the end but may be it is the wrong letter for the drive by windows term.

## ## End Default Options ##
+

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ac2e1f53-d583-4201-a2c1-ba9df08c0daf ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ac2e1f53-d583-4201-a2c1-ba9df08c0daf ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP 
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by TheBoat on 2008-02-13
Open the System Monitor (System -> Administration), then switch to the "File Systems" tab.  Which device corresponds to your XP files?  You can double click on them to see what is in them.

---

### Post by TheBoat on 2008-02-13
If you can't tell, then you can post the output of: ```
sudo fdisk -l
```

---

### Post by TheBoat on 2008-02-14
I am pretty sure that all you need to do is change this line > root (hd0,0)to this> root (hd0,1)but I can be sure if I have your output of:```
sudo fdisk -l
```

---

### Post by xoshnow on 2008-02-14
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcb6dcb6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         767     5798488+   b  W95 FAT32
/dev/sda2   *         768       11665    82388880    7  HPFS/NTFS
/dev/sda3           11666       25259   102770640   83  Linux
/dev/sda4           25260       25841     4399920    5  Extended
/dev/sda5           25260       25841     4399888+  82  Linux swap / Solaris
saman@saman-desktop:~$

---

### Post by TheBoat on 2008-02-14
Yeah, that is what you have to do. Change this> root (hd0,0)to this> root (hd0,1)

---

### Post by xoshnow on 2008-02-14
root (hd0,1) .....did the magic, ,  I was thinking about doing factory restore.... thank you The Boat you are a real cost guard.

---

