---
title: "this is how to reinstall GRUB and get ubuntu booting again"
date: 2007-05-02
forum: General Help
---

### Post by sdowney717 on 2007-05-02
simple enough 

boot computer from live cd
goto terminal window

TO SEE PARTITIONS
type sudo fdisk -l

ok, its a little confusing here next,

the root location of your ubuntu installation is what you need to know.

If its on a secondary drive in the first partition it will be (hd1,1)

type in terminal
   sudo grub 

the root partition is where you have ubuntu. In my case, it is on the secondary drive, first partition, sdb1 as shown in fdisk -l, this is most likely going to be the biggest partition you have for that drive.

SO, at terminal prompt type this to tell grub where your root partition is located.

>  root (hd1,1)

if it does not error, you may just have it right.

TO actually install grub here it is:
hd0 is the primary drive, hd1 is the secondary drive, etc....
to install boot grub on primary drive type:

> setup (hd0)  

to install boot grub on secondary drive type:  (good if you pull drive later and make it primary)

> setup (hd1)


my own fdisk -l is:

root@scott-desktop:~# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15260   122575918+   7  HPFS/NTFS

Disk /dev/sdb: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1190     9558643+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2            1191        1245      435645    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sdb5            1191        1244      433723+  82  Linux swap / Solaris
root@scott-desktop:~#

---

### Post by dcstar on 2007-05-02
There is a perfectly good "Tutorials and Tricks" sub-forum that has HOWTOs exactly like this already in it:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

People should not post things like this in any place other than that existing sub-forum, and then only after checking that something almost similar doesn't already exist.

The support question sub-forums are becoming increasingly cluttered with misguided (but obviously well intentioned) people posting all sorts of HOWTOs in them.

Because these posts exist all over the place in the Ubuntu forum, all this does is actually make it harder for people trying to find useful information rather than help them out solving their issues!

---

### Post by confused57 on 2007-05-02
This HowTo covers it very well:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
or
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
or
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

