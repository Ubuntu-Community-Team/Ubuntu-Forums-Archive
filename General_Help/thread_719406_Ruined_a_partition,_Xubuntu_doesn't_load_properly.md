---
title: "Ruined a partition, Xubuntu doesn't load properly"
date: 2008-03-09
forum: General Help
---

### Post by orduek on 2008-03-09
OK, Thats a long story but I'll try to short it out.
I got some old Celeron 700 computer and trying to make him an HTPC one (using Miro).
After some trials I managed to install Debian 4.0 but, I felt something was wrong so I decided to install Xubuntu (on a dual boot). The first time it divided the partition but didn't finish installation.
So, the second time I used the partition he did before, manually.
Everything worked great, and Xubuntu was working better then debian.
So, I decided to make the 10Gb Debian partition as some kind of Home partition.
I installed Gparted and deleted the Debian Partition and Formatted it.
Alas! now I can't write on that partition and everytime Xubuntu is loading it goes out and says something like, the check disk failed.
I have to write exit on the command prompt and it continues to load.
would love some help without the need to reinstall Xubuntu.

---

### Post by forestpixie on 2008-03-09
I'm guessing that when you formatted the UUID changed

once you've managed to boot

check the UUID's aginst the entries in fstab

blkid
cat /etc/fstab

if they don't agree - change the fstab entry

---

### Post by orduek on 2008-03-09
too much for me.
can you explain it in a bit simple way?

---

### Post by forestpixie on 2008-03-09
boot the pc - then go to terminal 

then post the output of these 2 commands

```
blkid
cat /etc/fstab
```

---

### Post by orduek on 2008-03-09
ormetal@HTPC:~$ blkid
/dev/hda1: UUID="c3ebce3c-a54c-4d12-bb18-1faeaf7adb7c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="c0655fa0-1ec4-4a38-a1d2-01362ffb955c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="61df6d0a-7aa6-479a-aad3-74bbacf95ce4" 
/dev/hda6: TYPE="swap" UUID="b3068ff1-86fd-4015-9d65-6225c687044c" 

and:
ormetal@HTPC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=c0655fa0-1ec4-4a38-a1d2-01362ffb955c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=305250d1-1e9d-49dd-a2ae-10bd60351ed2 /media/hda1     ext3    defaults        0       2
# /dev/hda5
UUID=61df6d0a-7aa6-479a-aad3-74bbacf95ce4 none            swap    sw              0       0
# /dev/hda6
UUID=b3068ff1-86fd-4015-9d65-6225c687044c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

any solutions?

---

### Post by forestpixie on 2008-03-09
> **orduek said:**
> ormetal@HTPC:~$ blkid
/dev/hda1: UUID="[COLOR="Red"]c3ebce3c-a54c-4d12-bb18-1faeaf7adb7c[/COLOR]" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="c0655fa0-1ec4-4a38-a1d2-01362ffb955c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="61df6d0a-7aa6-479a-aad3-74bbacf95ce4" 
/dev/hda6: TYPE="swap" UUID="b3068ff1-86fd-4015-9d65-6225c687044c" 

and:
ormetal@HTPC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=c0655fa0-1ec4-4a38-a1d2-01362ffb955c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=[COLOR="Red"]305250d1-1e9d-49dd-a2ae-10bd60351ed2[/COLOR] /media/hda1     ext3    defaults        0       2
# /dev/hda5
UUID=61df6d0a-7aa6-479a-aad3-74bbacf95ce4 none            swap    sw              0       0
# /dev/hda6
UUID=b3068ff1-86fd-4015-9d65-6225c687044c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

any solutions?

these should be the same, save fstab to a backup first and then open to edit

```
sudo cp /etc/fstab /etc/fstab.bak.0903
```

```
gksudo mousepad /etc/fstab
```

change the line to match the corresponding blkid result for that line - I suggest that you copy and paste it - save and reboot

ps why do you have 2 swap partitions?

---

### Post by orduek on 2008-03-09
I'll try that.
But, I deleted the Debian Partition so I don't really need the debian in my Grub, don't I?

---

### Post by forestpixie on 2008-03-09
not really - was debian on hda1 then - I assume so, once you've got it mounting you could leave it alone or use it for storage

if you don't want to mount the partition at all comment out the offending line in fstab

if you don't want to see it on the menu.lst you can edit it, post it here if you're not sure

---

### Post by orduek on 2008-03-09
OK. That did the trick and Xubuntu is loading great now. Thanx.
But I can't write on the hda1 partition anymore, even after trying to format it again.
how can I change that? because now I can't even use it for storage :(

---

### Post by forestpixie on 2008-03-09
that's down to permissions then - not too sure about that - can have a look into it later

have a search for permissions - start looking here
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by forestpixie on 2008-03-10
this could help

[http://ubuntuforums.org/showthread.php?t=720223](http://ubuntuforums.org/showthread.php?t=720223)

---

### Post by Zarckon on 2008-03-10
I'm having a similar problem. I followed the instructions here, but still crash on boot. The specific fault I get is is with fsck.

Failed to open the device. Gives the UUID and ends with "No such file or directory". The beginning of the error indicates that it's failing on /dev/hda2, but gives the UUID for /dev/hda4. I made sure that the UUID's matched in fstab with the output of blkid.

Originally the fstab file had no hda4, but did have hda5 and hda6. I deleted 6 and changed 5 to 4 (that was the one with the correct UUID). I made an hda4 directory in /media and /dev has hda4 listed. I figure I must be missing another place to list it (or doing something else equally stupid). Any thoughts on where I'm going wrong? Thanks in advance.

---

### Post by forestpixie on 2008-03-10
:Zarckon - can you post blkid, cat /etc/fstab and sudo fdisk -l

---

### Post by Zarckon on 2008-03-11
K, I can do that.

blkid

> /dev/hda2: UUID="9A9B-57ED" TYPE="vfat"
/dev/hda3: UUID="dd147e59-b7d2-4e09-9122-9514e578c18d" TYPE="reiserfs"
/dev/hda1: UUID="F8A0-D7B0" TYPE="vfat"
/dev/hda4: UUID="8d8d9338-e6eb-4ce3-adc8-efc6fd421203" TYPE="reiserfs"

fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=dd147e59-b7d2-4e09-9122-9514e578c18d /               reiserfs notail          0       1
# /dev/hda1
UUID=62157E987475196E /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=9A9B-57ED  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=8d8d9338-e6eb-4ce3-adc8-efc6fd421203 /media/hda4     reiserfs defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

fdisk

> Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4363a0a2

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   b  W95 FAT32
/dev/hda2            2433        9119    53713327+   b  W95 FAT32
/dev/hda3            9120       15806    53713327+  83  Linux
/dev/hda4           15807       30401   117234337+  83  Linux

Well, there it is. Hope that helps. Thanks.

---

### Post by Zarckon on 2008-03-11
K, I found it. Knew it was something stupid I was missing. The UUID for hda1 was not the same in blkid and fstab. I had not seen that, having the mind set that it was okay since hda2 was being complained about on boot and hda4 had the identity problem (and being lazy and having seen that the UUID in 2 and 3 was fine, 1 had to be. lol).

Thanks for recommending that I post blkid and fstab even though I was sure they were okay. Staring at them in the forum was actually easier to see than on the console screen.

Peace out.

---

