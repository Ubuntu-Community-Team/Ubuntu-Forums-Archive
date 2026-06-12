---
title: "Cannot mount a Partition after reinstalling windows xp"
date: 2007-03-11
forum: General Help
---

### Post by true_friend on 2007-03-11
Hi folks
i am facing a serious problem. last day reinstalled my windows xp on C:(/dev/hda1) it was FAT32 now changed to NTFS. But the problem is now other partition E:(/dev/hda8) it cannot be mounted  automatically at startup. i tried to mount it through KDE System Settings but it gives error same error i got through "sudo mount -a" command this is the out put.
.........................
ss@ss-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda8,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
==================
i can mount this partition manually with sudo mount /dev/hda8 /media/hda8 but then it is not accessable i can only access it through root account and there i also cannot write something.
i tried to change permission but could not.
any ideas????
Edgy is once again teasing me a lot last time i had to migrate back towards Dapper i do not want this now.:mad: 
Thnx for reading it.
Regards
True_Friend

---

### Post by true_friend on 2007-03-11
This is fstab output
==============================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda6 -- converted during upgrade to edgy
/dev/hda6 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1 -- converted during upgrade to edgy
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000,loop,uid=0,gid=0,auto,rw,nouser 0 0
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5 /media/hda5 vfat iocharset=utf8,umask=000,loop,uid=0,gid=0,auto,rw,nouser 0 0
# /dev/hda8 -- converted during upgrade to edgy
/dev/hda8 /media/hda8 vfat umask=0000 0 0
# /dev/hda9 -- converted during upgrade to edgy
/dev/hda9 /media/hda9 vfat iocharset=utf8,umask=000,loop,uid=0,gid=0,auto,rw,nouser 0 0
# /dev/hda7 -- converted during upgrade to edgy
/dev/hda7 none swap sw 0 0
================================================
dev hda8 was also same as other windows partitions but i changed it to vfat umask=0000 0 0 thinking may it would solve the problem but invain.
i got this superblock problems before also thats why i had to made these changes in code
"oop,uid=0,gid=0,auto,rw,nouser 0 0"
i had read about it some where.
plz help me.

---

### Post by Kateikyoushi on 2007-03-11
Change the hda8 line to look like this.

```
/dev/hda8    /media/hda8 ntfs  nls=utf8,umask=0222 0    0
```

---

### Post by true_friend on 2007-03-12
thnx it was ok
i formatted hda8 and convertad back it to fat32 i hate ntfs it does not supported well on linux.

---

### Post by Kateikyoushi on 2007-03-12
Were you able to change the fstab entry and mount it after changing the filesystem ?

---

