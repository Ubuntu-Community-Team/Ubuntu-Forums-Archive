---
title: "Please Help me with the fsck"
date: 2007-03-25
forum: General Help
---

### Post by desper on 2007-03-25
My feisty boot failed at 

> file system check

I can still run into the system by "reboot" command, funny..though.

The checkfs log in var/log/fsck shows this,

> fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=2ee6379a-6969-407b-9361-c96aa2532c50'

fsck died with exit status 8

Really need help!
Thanx in advance

---

### Post by desper on 2007-03-25
[COLOR="Red"]Not[/COLOR] solved, i replaced the uuid in grub/menu.lst with the /dev/sda5 [my root]

---

### Post by boivie on 2007-04-30
I got the same problem after replacing one of my linux partitions with pc-bsd, without telling ubuntu about the change. 

My guess is that fsck is trying to access a partition, and cannot find it in the way it used to be.

---

