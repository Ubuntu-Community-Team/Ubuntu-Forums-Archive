---
title: "Automatically mount FAT32 on startup"
date: 2008-05-01
forum: General Help
---

### Post by don_emilio_juan on 2008-05-01
Hello,

I ve upgraded to Hardy lately and on start up it does not mount my FAT32 partition automatically. It does mount though my FAT32 external usb drive.

What do I have to do to mount the internal FAT32 partition automatically on startup? Is there a convenient tool to do that and manage partitions and access rights etc?

Thank you & best
Juan

---

### Post by elvinatom on 2008-05-01
add to the fstab:
```
/dev/hda1 /media/my_fat_partition vfat defaults,umask=0000 0 0
```
where "hda1" must be replaced by your fat32 device and "/media/my_fat_partition" must be replaced with your desired mount-point. If you have trouble understanding what I mean, let me know - I can give you a step-by-step walkthrough ;-)

---

### Post by Tulainas on 2008-05-02
> **elvinatom said:**
> add to the fstab:
```
/dev/hda1 /media/my_fat_partition vfat defaults,umask=0000 0 0
```
where "hda1" must be replaced by your fat32 device and "/media/my_fat_partition" must be replaced with your desired mount-point. If you have trouble understanding what I mean, let me know - I can give you a step-by-step walkthrough ;-)
---------------------------


Hey, I`ve got littl probs here...!

I tried your trick but I still have to mount it myself. let m post you my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=5777f806-b5e0-4cc7-915d-2b95fd068cf8 /               ext3    relatime,errors=remount-ro 0       1
[SIZE="5"]# /dev/sda5  /media/DataStorage    vfat    utf8,umask=007,gid=46 0       0[/SIZE]
# /dev/sda6
UUID=e7ae107c-c662-474e-8460-7e1e98012f05 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
[SIZE="5"]/dev/hda1       /media/Richter  ntfs    nls=utf8,umask=0222   0    0[/SIZE]

so, those are my SATA disk parttions, What can  modify (and where) to mak them automount at startup? I used to se them right after booting up in 7.04

What's dfferent now?

ALso, USB drives doesn't automount either... doy you have any Idea?

Thaks!

---

### Post by mojorising on 2008-05-02
Maybe type fdisk -l at the command line to make sure you are mounting the right devices. Also, make sure the mount points specified in fstab exist. Silly, I know, but those are some guesses. It pays to check the easy things too. 

You might want to have a look at this classic Red Hat document that explains how to do what you are trying to do quite well:

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-q-and-a-windows.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-q-and-a-windows.html)


Mike

---

