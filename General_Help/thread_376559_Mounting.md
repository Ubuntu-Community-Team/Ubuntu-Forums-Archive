---
title: "Mounting"
date: 2007-03-05
forum: General Help
---

### Post by chewy110 on 2007-03-05
Hi,
I'm trying to mount my Windose NTFS partition with no luck. Using the NTFS-3g method ([http://www.arsgeek.com/?p=675#comment-17264](http://www.arsgeek.com/?p=675#comment-17264)) I have noticed my fstab(\etc) doesn't show a UUID for it.:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=f7d4c838-680e-4b62-a3d1-764af6889409 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=d06400ce-f789-46ea-9e60-3b2fd3b5aaf8 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /media/sda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

Any ideas on how to solve this?
I have posted on ArsGeek where i got the method, comment no.32:
[http://www.arsgeek.com/?p=675#comment-17264](http://www.arsgeek.com/?p=675#comment-17264)  but no reply yet..............

Please help me so i can use my docs in windows.

TY :KS

---

### Post by zvacet on 2007-03-05
[http://easylinux.info/wiki/Ubuntu_Edgy]("http://easylinux.info/wiki/Ubuntu_Edgy")

---

### Post by chewy110 on 2007-03-05
thank you for your reply. 

i folowed those mounting instructions to the letter but it still hasn't fixed my problem of there being no UUID in /etc/fstab for my windows ntfs mount.

anyone else have any ideas as i'm getting fed up.

p/s if your going to send me a link please be polite enough to explain the reason why.........

---

### Post by chewy110 on 2007-03-07
anyone?

---

### Post by chewy110 on 2007-03-07
all sorted now thanks everyone for your help!
:)

---

