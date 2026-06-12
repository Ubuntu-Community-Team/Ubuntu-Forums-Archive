---
title: "Why can't I unmount my drives?"
date: 2007-11-11
forum: General Help
---

### Post by mmilitia9 on 2007-11-11
Hi everyone,

I've been using 7.10 since release.  Everything has worked fine.  I decided to give it a fresh install for the heck of it because of a few errros I had last time.. Which corrected it's self(thank god).  The only problem now is..
I have SDA1 and SDA2 partitions sitting on my desktop.  That's awesome.. but I only want to access them when I feel like it.  When I go to unmount them it tells me I don't have permission and need to be root.

This didn't do this before... soo, what's the matter now?

Thanks in advance,

Dominick

---

### Post by mcduck on 2007-11-11
If those drives are mounted at boot as configured in /etc/fstab, only root is able to unmount them (because root has mounted them). If you don't want them to be mounted automatically edit the file and add 'noauto' to their mount options.

---

### Post by mmilitia9 on 2007-11-11
GNU nano 2.0.6                           File: /etc/fstab                                                             

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b2d21622-bac0-4df3-9e9e-69b4c28a2031 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E8ECB364ECB32C26 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=156e379f-dc7b-44cc-9f33-ddde295033df /media/sda4     ext3    defaults        0       2
# /dev/sda5
UUID=fac2bc7f-7ede-4d5a-a4ed-62973cb8e4c2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


That's what I see... Where do I add the "noauto" ?

---

### Post by rsambuca on 2007-11-11
I don't know why sda2 is showing on your desktop since that is your '/' partition.

---

### Post by mcduck on 2007-11-11
```
# /dev/sda1
UUID=E8ECB364ECB32C26 /media/sda1 ntfs noauto,defaults,umask=007,gid=46 0 1
```

I don't know about sda2, as it's your root and shouldn't be mounted twice. If you open it from your desktop does it open your actual root partition or something else? If it's something else there could be something wrong with the UUID's in your fstab. You can check the correct ones with the 'blkid' command.

---

