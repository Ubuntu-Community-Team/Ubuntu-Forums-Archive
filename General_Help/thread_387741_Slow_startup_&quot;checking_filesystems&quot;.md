---
title: "Slow startup: &quot;checking filesystems&quot;"
date: 2007-03-18
forum: General Help
---

### Post by jackn on 2007-03-18
My Edgy Eft install starts up less fast than my Dapper used to.

This is due to another step that has been added: "Checking filesystems". I'm not aware of having asked for such a check, and I don't think it's a default.

The screen says that since  /dev/hda6 "has been mounted 30 times" without being checked, a check is carried out. But this happens upon every startup... 

How can I get rid of this constant checkup? Preferably, I'd like to leave the proper (apparently every 30 times) systemfile check intact...

Thanks,
Jackn

---

### Post by mcduck on 2007-03-18
Could you post outputs of  'sudo fdisk -l' and 'cat /etc/fstab' here? Theres probably something wrong in your fstab.

---

### Post by jackn on 2007-03-19
Here are the outputs you called for, mcduck:

```
sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3173    25487091    c  W95 FAT32 (LBA)
/dev/hda2            3174        4389     9767520   83  Linux
/dev/hda3            4390        4998     4891792+   5  Extended
/dev/hda5            4876        4998      987966   82  Linux swap / Solaris
/dev/hda6            4390        4875     3903732   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 15.3 GB, 15393079296 bytes
255 heads, 63 sectors/track, 1871 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         446     3582463+  83  Linux
/dev/hdb2             447        1871    11446312+  83  Linux
```




```
jackn@Phoenix:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=7d2b9c04-4ebe-423e-a130-1399b55033a4 / ext3 defaults,errors=remount-ro,user_xattr 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=e4eff110-c886-4d23-915b-4aef5611ba4a /home ext3 defaults,user_xattr 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=4F45-1C3A /media/hda1 vfat defaults,utf8,umask=007,gid=46, 0 1 
# /dev/hda5 -- converted during upgrade to edgy
UUID=278bd9d1-ed7c-4b5c-b906-d310247618bc none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

BTW, is it a security risk to post the above data, te UUID's, for example? Not meant personally, of course, but just wondering about proper protocol.

Thanks kindly for the prompt response.
Jackn

---

### Post by mcduck on 2007-03-19
No, the UUID is just a cheksum calculated from your partition info to allow Linux to recognize the drive/partition even if you swap the places of drives in your computer. None of that information is any security risk, we actually have a thread in Cafe where everybody is posting their 'cat /etc/fstab' outputs, just for fun of it..

Anyway, try changing the last '1' in the enrty for your FAT partition into '0'. This number tells your system the order in which the fsck should check the partitions, '1' should only be used for /, and for others you can either use '2' (to check them after /) or '0' to not check them at all.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=7d2b9c04-4ebe-423e-a130-1399b55033a4 / ext3 defaults,errors=remount-ro,user_xattr 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=e4eff110-c886-4d23-915b-4aef5611ba4a /home ext3 defaults,user_xattr 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=4F45-1C3A /media/hda1 vfat defaults,utf8,umask=007,gid=46, 0 0 
# /dev/hda5 -- converted during upgrade to edgy
UUID=278bd9d1-ed7c-4b5c-b906-d310247618bc none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

BTW, the check for partitions is and has always been default feature, it should happen every 30 times the partition is mounted. Problem is that FAT can't store the information about when it was last time checked.. Anyway, try that change first, even when it doesn't actually change settings for hda6 it might solve the problem anyway..

---

### Post by jackn on 2007-03-19
Carried out the advice, and... it worked a treat.

Prompt response appreciated.

On top of it, learned a lot...

Hearty thanks, mcduck.

Jackn

---

