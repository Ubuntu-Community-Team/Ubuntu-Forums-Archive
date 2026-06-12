---
title: "Ubuntu Feisty booting really slow"
date: 2007-06-03
forum: General Help
---

### Post by robertpolson on 2007-06-03
Fresh install of Ubuntu Feisty and the problem I get is the famouse:

"kinit: no resume image found" which occurs half way through the booting process. I still have no idea how to get rid of this thing as it slows down the boot for like 40 seconds or so.

I read somewhere that this could be a problem of UUID of the swap partition, so what I did was using Gparted I reformatted my swap partition again. After that I got some strange booting messages, so to fix things up I went to my:

/etc/samba/smb.conf  and use blkid to check that everything is setup correctly. 

I did that and what I get now is that when Ubuntu loads half way, I get a message saying 

"Loading, Please Wait" and it stays there for like 50 seconds and the the booting process resumes and boots fine.

Help ! Please.

Here is my fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=86154335-b431-4299-b8f1-a705c7bc949e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fc86924e-50e1-47f6-b167-5c5ec91b249d /home           ext3    defaults        0       2
# /dev/sda3
UUID=a60effb8-70a1-4d68-915f-18d284794c56 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Here is blkid

> /dev/sda1: UUID="86154335-b431-4299-b8f1-a705c7bc949e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="a60effb8-70a1-4d68-915f-18d284794c56" TYPE="swap" 
/dev/sda5: UUID="fc86924e-50e1-47f6-b167-5c5ec91b249d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="Movies" UUID="7d96e80a-7ee8-4356-b791-087363d63012" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="MediaDrive" UUID="22e4a3d4-ecd1-44fb-b6da-65e3bbe526ba" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: LABEL="Audio" UUID="ef2a2c18-c6da-4f13-b725-3d51c689e2cf" SEC_TYPE="ext2" TYPE="ext3" 

---

### Post by robertpolson on 2007-06-04
I'll run a few more tests. I think it boots fine now.

---

### Post by robertpolson on 2007-06-04
Yeah, it boot fine now.

---

### Post by Pat123 on 2007-06-25
I have a similar issue...will try this out and see if it works for me too !!

---

