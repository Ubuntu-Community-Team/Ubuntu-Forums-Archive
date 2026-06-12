---
title: "2 Ubuntu Feisty 7.04 Live cd's - Produce 2 different installations - why?"
date: 2007-05-22
forum: General Help
---

### Post by darkworld on 2007-05-22
I have a livecd Feisty 7.04 downloaded from the Ubuntu site that sets my pc drives up in the /dev/sdx SCSI format.

But I also have a Ubuntu Feisty 7.04 livecd that Ubuntu posted to me that sets my pc up in the /dev/hdx format.

Discovered this purely by chance. Whats is going on? Its not a problem but I would like to understand.

---

### Post by confused57 on 2007-05-22
> **darkworld said:**
> I have a livecd Feisty 7.04 downloaded from the Ubuntu site that sets my pc drives up in the /dev/sdx SCSI format.

But I also have a Ubuntu Feisty 7.04 livecd that Ubuntu posted to me that sets my pc up in the /dev/hdx format.

Discovered this purely by chance. Whats is going on? Its not a problem but I would like to understand.

By posted, do you mean free cds received from Shipit?  If so, they're Ubuntu Dapper 6.06...The final release of Feisty recognizes all hard drives as SATA, i.e. sda, sdb, etc...if you happen to have a Feisty pre-final release version, your hard drives may have been recognized as hda or sda.

---

### Post by darkworld on 2007-05-22
i mean free cd's posted to me from ubuntu, using cd request on site. Below is what I get. 


>  lsb_release -a

> No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

 > cat /etc/fstab


> # /etc/fstab: static file system information.
#
I## <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e5b48529-bf32-4476-b8e5-e194f0db458e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID=eb396626-2aaa-4dd5-988d-59a1cc5cdaa5 /home           ext3    defaults        0       2
# /dev/hda1
UUID=A0B04CA3B04C8230 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb9
UUID=f1b17a1e-0d3a-4c84-ad6a-a2e4fe6e950d /opt            ext3    defaults        0       2
# /dev/hdb7
UUID=567bdca6-f2e8-48a1-a125-78ae264db0b8 /tmp            ext3    defaults        0       2
# /dev/hdb10
UUID=280286a1-e6f7-47f2-8363-dfe26c45d5f7 /usr            ext3    defaults        0       2
# /dev/hdb8
UUID=05244778-1c40-40ee-b24d-f3025e5948cb /var            ext3    defaults        0       2
# /dev/hdb5
UUID=d604970e-c998-482e-ac33-2d51f1d899dc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I am well happy with this because the other installation was nothing but problems! I thought maybe this was an improved feisty. Anyway thanks it seems i must have a pre release. I guess there will be a few other confused peeps.

---

### Post by confused57 on 2007-05-22
Thanks for the heads-up, I didn't realize Shipit was sending free Feisty cd's(I need to visit the Ubuntu homepage more often).  You might try running "uname -r" or "uname -a" on both the live cd's, just to see if there's a kernel version difference?  I prefer the hda & sda designation of hard drives also, it's definitely a little confusing to have my hda listed as sda, and my sda listed as sdb.

---

### Post by darkworld on 2007-05-22
Ok this is what I get from the disk that loads up the hdx format illustrated earlier in thread.
> 
ubuntu@ubuntu:~$ uname -r
2.6.20-15-generic

and 
> 
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

now im hunting for the sdx format disk......

---

### Post by darkworld on 2007-05-22
Ok ive found a disk which I think is the other disk. cant be sure because I burnt a couple.

So for the point of the exercise I guess its pretty useless .......it gives the exact same read out as above! ??? What do you make of that?

Im well impressed with the pre release, several packages run that didnt in the other version. Think im going to re release this as Not_to_Feisty 7.05 lol

---

