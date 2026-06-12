---
title: "Volume Mounting"
date: 2007-10-02
forum: General Help
---

### Post by w116tjb on 2007-10-02
Can someone please explain how to have a volume mount at startup? I have my music files on my other NTFS hard drive and I'm getting tired of having to mount the volume before I fire up Amarok. 

Less of this: :confused:

More of this: :guitar:

Thanks!

---

### Post by Rocket2DMn on 2007-10-02
Is your volume internal or external?
If it is detected at startup (which it should be if it is internal or an always on external), you probably just need to add an entry in /etc/fstab
Please post the output of
```
sudo fdisk -l
cat /etc/fstab
```  We'll go from there.

---

### Post by w116tjb on 2007-10-02
Internal. 

This is the hard drive I want to mount at startup.
> Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdca3dca3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=38f00646-0599-4591-b022-8c8a8f9e9538 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1e7b4f31-2851-4e85-aa6c-979b0376b5f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by Rocket2DMn on 2007-10-02
OK, so assuming /dev/sdb1 is the drive you want to automatically mount, add this line at the end of your fstab file
```
/dev/sdb1 /media/music ntfs-3g defaults,locale=en_US.utf8 0 0
```  You can replace "music" with whatever you want, but you need to create the folder under /media by running
```
sudo mkdir /media/music
```
You can edit the fstab file by running
```
gksudo gedit /etc/fstab
```
Once you have the file edited and saved, run
```
sudo mount -a
``` That mounts everything in your fstab file.  The drive should now mount automatically when you reboot the computer.

---

### Post by vinutux on 2007-10-02
there are many ways...............

take a easy and hassle free way

just install a pakage called [COLOR="Red"]ntfs-3g[/COLOR]

for this open terminal and type sudo apt-get install ntfs-3g

                    or

open synaptic and search ntfs-3g and install it


after install go to applications--> system tools---> ntfs configuration tool and activate enable read and right support for ntfs filesystem .......done recomended and easy way simple too like ubuntu ...............................:lolflag::lolflag::lolflag:

---

### Post by w116tjb on 2007-10-02
Awesome! Thanks Rocket2DMn, it worked perfectly after reboot.

vinutux, I'm using Gutsy, which to my knowledge already has ntfs-3g included in it, though it doesn't have the menu option like in Feisty. Thanks though. I appreciate the effort.

---

### Post by dcstar on 2007-10-02
> **w116tjb said:**
> Can someone please explain how to have a volume mount at startup? I have my music files on my other NTFS hard drive and I'm getting tired of having to mount the volume before I fire up Amarok. 
......

Actually if you install the **pysdm** package, it will write the fstab entries for you.

It's a nice little tool for users doing this sort of thing and it baffles me why it isn't part of the base install.

---

