---
title: "Advice on external ntfs drive"
date: 2007-02-28
forum: General Help
---

### Post by Pugwash on 2007-02-28
Hi,

I installed ubuntu a couple of weeks ago and I managed to some how set up ntfs write support initially using one of the tutorials on the net ( I don't remember which one or how I did it). I've not had any problems since then but I have a suspicion that I may have set it up wrong due to inexperience, and that there may be a risk that I might be causing filesystem corruption on my external ntfs usb drive. So I started to  dig around my computer today trying to figure out how I might have done it. This is what I get by running  "sudo fdisk -l":

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS


```

My external drive is "/dev/sdb1" I presume. But it doesn't seem to be listed in my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


```

Could any of the wise people here explain how exactly its working and give me some peace of mind please. I'm still pretty much a noob. I'd greatly appreciate it. 

Many thanks

Pugwash

---

### Post by Bubs on 2007-03-05
do you remove it often?  as in do you have your system running then you plug it in do stuff then remove it?  or do you have it pluggen in and it stays pluggen in?

  from what I know (which is limited) it won't show up in the fstab unless you put it there.  and its best not to if you remove it often.  you can just plug it in and it auto mounts for you. 

 I don't know much about ntfs support, one of my drives works and the other is r/o don't know why, but I think if it works and you haven't had problems don't worry.  but just in case back up you **** and do a few test runs for a week or so and see what happens.

---

### Post by Pugwash on 2007-03-10
> **Bubs said:**
> do you remove it often?  as in do you have your system running then you plug it in do stuff then remove it?  or do you have it pluggen in and it stays pluggen in?

  from what I know (which is limited) it won't show up in the fstab unless you put it there.  and its best not to if you remove it often.  you can just plug it in and it auto mounts for you. 

 I don't know much about ntfs support, one of my drives works and the other is r/o don't know why, but I think if it works and you haven't had problems don't worry.  but just in case back up you **** and do a few test runs for a week or so and see what happens.

Thanks for the reply, sorry for the late response, I didn't see your reply. I had to reinstall ubuntu yesterday and I followed the proper method listed here -http://www.ubuntuforums.org/showthread.php?t=217009 . I followed the automatic configuration method, pretty simple. I think you'd probably be better of following the manual method for multiple drives, but I'm not sure either.

Cheers

---

