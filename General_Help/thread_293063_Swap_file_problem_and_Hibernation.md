---
title: "Swap file problem and Hibernation"
date: 2006-11-04
forum: General Help
---

### Post by btboudreaux on 2006-11-04
Ever since upgrading to Edgy, my swap file (I don't have a swap partition) won't mount on startup. I noticed my fstab looks different. Now everything has a UUID. How do I get the swap file to mount? I have gotten it to mount again with mkswap and swapon. I just need it to keep mounting on startup.

Here is my fstab.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=7c6aa7e6-4851-489f-8d2d-8635377c12fa / ext3 defaults,errors=remount-ro 0 1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=03E0536C2577548B /media/ntfs1 ntfs nls=utf8,umask=0222 0 0
/mnt/856Mb.swap none swap sw 0 0

Also, I could never get Hibernate to work. Suspend works fine but Hibernate has never worked for me (even in Dapper). I have a HP Pavilion zv6000 laptop. Even when I manually mount the swap file, hibernate still doesn't like my laptop. Any suggestions? or do I just have to wait until my particular laptop is more supported?

Alright, Thanks in advance for any help!

---

### Post by btboudreaux on 2006-11-07
no one can tell me why my swap file won't mount?

---

### Post by arrizaba on 2006-11-09
got the same problem. No swap. Hope someone helps, cause after using the computer for some hours there's no memory left and the programs struggle to start....:(

---

### Post by feest on 2006-11-09
well i had this problam once before on an other linux (damn small)(well i dont know acutally if its not neseccary or a bug) but it doesn't use its swap, it does if i create it on install

---

### Post by mbeierl on 2006-11-09
Just a wild guess, but try reformatting the swap file - just in case it got corrupted:

sudo mkswap /mnt/856Mb.swap

and then try

sudo swapon -a

---

### Post by btboudreaux on 2006-11-09
> **mbeierl said:**
> Just a wild guess, but try reformatting the swap file - just in case it got corrupted:

sudo mkswap /mnt/856Mb.swap

and then try

sudo swapon -a

Did that. It mounts the swap and it works until you reboot then you have no swap once again.

---

### Post by tobyw01 on 2006-11-09
I had the same problem. I fixed it with these instructions.

[https://launchpad.net/distros/ubuntu/+bug/66637/comments/23](https://launchpad.net/distros/ubuntu/+bug/66637/comments/23)

---

