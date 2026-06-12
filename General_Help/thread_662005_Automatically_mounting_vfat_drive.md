---
title: "Automatically mounting vfat drive"
date: 2008-01-08
forum: General Help
---

### Post by PRC on 2008-01-08
Hi all,

I have a vfat drive shared between Ububtu and the devil from Redmond.

I have two users in Ubuntu and would like to mount the shared drive automatically for both.

Using info found here [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) I have modified /etc/fstab to look like this :-
( My added line is the last one in the file ).

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=84cbc494-9004-4c7c-9ebb-9325912d4469 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=72E4925BE4922201 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=43cd9a55-a39a-432b-b387-8742f722bbeb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1  /media/disk  vfat  user,auto,fmask=0111,dmask=0000  0  0

This causes the drive to mount fine for my main user but not the second user.

Any suggestions?

Thanks,

Paul C

---

### Post by capink on 2008-01-08
make a group called vfat with gid 1005 and added all users to it.

and modify the vfat partition options as follows:

```
UUID=replace       /mount/point        	 vfat    defaults,utf8,umask=007,[COLOR="Red"]gid=1005[/COLOR] 0       0
```

---

### Post by reckless2k2 on 2008-01-08
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

that should help you.

---

### Post by PRC on 2008-01-09
Great stuff!

Thanks for the input,using the info suggested I used the following line in my fstab

/dev/sdb1  /media/disk  vfat  iocharset=utf8,umask=000  0    0

This line works fine - so problem solved, but how about a suggestion as to why compared to this line which did not work

/dev/sdb1 /media/disk vfat user,auto,fmask=0111,dmask=0000 0 0

Thanks again

Paul C

---

### Post by reckless2k2 on 2008-01-09
sorry i couldn't answer to why your other line didn't work. dmask and fmask may be phased out or it could possibly be that *mask works with only 3 numbers. i think you might have had too much going on. not sure. haha. be sure to thank.

 i'm only here for the thanking praise. haha

---

### Post by Lostincyberspace on 2008-01-09
your were setting it to user which means administrator basically. It is still there but you have to go there manually through /media/sdb1.

---

### Post by dcstar on 2008-01-09
> **PRC said:**
> Hi all,

I have a vfat drive shared between Ububtu and the devil from Redmond.

I have two users in Ubuntu and would like to mount the shared drive automatically for both.

Using info found here [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) I have modified /etc/fstab to look like this :-
.......

Or you could have simply installed the **pysdm** package, and set up the mount with a few minutes work in System-Administration-Storage Device Manager.

---

