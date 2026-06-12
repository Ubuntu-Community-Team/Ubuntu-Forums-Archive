---
title: "Can't read logical drives, no UUID number?"
date: 2007-11-25
forum: General Help
---

### Post by don_m on 2007-11-25
I upgraded from 7.04 to 7.10. It seems that the upgrade did not allow my hda5 and hda6 vfat drives to be read. I noticed the other drives have the UUID indentifier. Here is my fstab file:

[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=57d0ab52-fcf7-4245-94dc-d6fb543bb70f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F6F47CF1F47CB609 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=28A5-B76B  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=61d528dc-c748-4355-8ecd-ae3c0570ff2f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0[/FONT]

What do I need to do to be able to read hda5 and hda6?

---

### Post by sisco311 on 2007-11-25
you can use the```
sudo vol_id -u /dev/**hdaX**
```command to get the uuid of your partitions.

---

### Post by don_m on 2007-11-25
I tried that, but get errors. :confused:

[FONT="Courier New"]vp@vp-desktop:/etc$ sudo vol_id -u /dev/hda5
[sudo] password for vp:
/dev/hda5: error opening volume
vp@vp-desktop:/etc$ sudo vol_id -u /dev/hda6
/dev/hda6: error opening volume
vp@vp-desktop:/etc$ sudo vol_id -u /dev/hda5
/dev/hda5: error opening volume
[/FONT]

---

### Post by Chymera on 2007-11-25
I got smth similar, you can uncomment those lines in your fstab and then you won't get any error at startup, but i still don't know how to get them mounted....

here's my case:[http://ubuntuforums.org/showthread.php?t=622404](http://ubuntuforums.org/showthread.php?t=622404)

---

### Post by benerivo on 2007-11-25
You can get the UUID's with```
blkid
```

---

### Post by don_m on 2007-11-25
Okay, I did the blkid thing, and ended up changing this part of the fstab to this:

[FONT="Courier New"]# /dev/hda1
UUID=F6F47CF1F47CB609 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
UUID=00000D48	      /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0 1
UUID=00000D49         /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0 1
# /dev/hdb1[/FONT]

I did a sudo mount -a, and it tells me that the hda5 and hda6 do not exist. I checked the format of hda5 and hda6 against my laptop and other than UUID, it looks the same. 

Anything else I can try?

---

### Post by benerivo on 2007-11-26
You could try a basic command line mount with```
sudo mkdir /media/test
sudo mount /dev/hda5 /media/test
```to see if that works. You could also try installing GParted Partition Manager and using that to see what info it shows on the drives. If you can back up all your data on them, I would then recommend using GParted to delete the partitions and remake them (ideally as ext3 if feasible) to see if that fixes the problem with them.

---

### Post by don_m on 2007-12-01
Okay, here are the results:

[FONT="Courier New"]
vp@vp-desktop:/$ sudo mkdir /media/test
[sudo] password for vp:
vp@vp-desktop:/$ sudo mount /dev/hda5 /media/test
mount: special device /dev/hda5 does not exist
[/FONT]

I still don't see why this is happening. The two partitions worked great starting with 6.06 version. I have win2k and Ubuntu on my drives. I like using the Opera browser and having some of the files be accessible to more than one operating system.

---

