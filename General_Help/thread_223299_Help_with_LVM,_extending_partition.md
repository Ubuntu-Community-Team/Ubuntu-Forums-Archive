---
title: "Help with LVM, extending partition?"
date: 2006-07-26
forum: General Help
---

### Post by Daniel15 on 2006-07-26
Well, I'm using LVM on my Ubuntu server, but I was running out of disk space. So, seeing as I'm using LVM, I decided to add a new hard drive to the system, and extend the logical volume group, and the partition (I have two partitions, one for /home, the other for the root file system). I managed to use 'pvcreate' on the new drive, and 'vgextend'/'lvextend' to extend the group (seeing as Webmin didn't seem to like working with LVM). However, even though the volume group (or logical volume or whatever it's called, the /dev/mapper/main-main thingy) is now 8 GB, the partiton is still stuck at 4 GB (I added an extra 4 GB hard drive).

Someone told me that I need to 'extend' the ext3 partition using some utility (resize2fs maybe?), but I have no idea how to do so (as the partition is mounted -- it is the root file system).


Any help with this would be appreciated :D

--Daniel15

---

### Post by zitch on 2006-07-26
From [http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

Looks like for an ext3 filesystem, you'll have to unmount, tell it to resize, then mount it again.  for example:

```
   # umount /dev/myvg/homevol/dev/myvg/homevol
   # resize2fs /dev/myvg/homevol
   # mount /dev/myvg/homevol /home
```

Since it's your root filesystem, you may have to boot up with the live CD to extend it...  Some one else may have to help with that.

---

### Post by Daniel15 on 2006-07-27
Thanks for the suggestion about using the Live CD. I never thought about approaching it that way (now that you mention it, it seems so simple). I don't have access to this computer at the moment, but I'll try it about this time tommorow and see how it goes :)

EDIT: Also, is there a way to 'de-extend' a partition? I added a 4 GB hard drive, but I will be getting a second-hand 10 GB hard drive. Seeing as none of the space on the 4 GB has been used (as I said above, the partition is still the old size), is it possible to remove the 4 GB hard drive, and add the 10 GB one? (I guess that this would mean somehow reducing the size of the volume group, and then adding the new hard drive)

EDIT 2: Bleh, I just checked the link you sent, and the next page after it is '**11.10. Reducing a logical volume**'... I guess that solves that problem ;)

---

### Post by Daniel15 on 2006-07-27
[double post. please remove]
Where's the delete button?

---

### Post by Daniel15 on 2006-07-29
OK, I suppose it doesn't matter anymore. I accidentally destroyed the partition in an (unrelated) incident, so I just reinstalled Ubuntu (this time, with the 10 GB hard drive).  Everything is working as I'd like it too

Thanks for all your help. That information will be useful for me in the future :)

---

