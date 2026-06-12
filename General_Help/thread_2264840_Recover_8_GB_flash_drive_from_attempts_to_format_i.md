---
title: "Recover 8 GB flash drive from attempts to format it"
date: 2015-02-10
forum: General Help
---

### Post by michael-piziak on 2015-02-10
I attempted to format my 8 gig flash drive in different formats, using Gparted and Disk Utility so I could put a larger file on it than what was previously allowed.

Now I can't get Ubuntu 12.04 lts to recognize the flash drive when I insert it.

I can still see it in gparted or Disk Utility.  I've formatted it the regular way I think, but it still doesn't show up.

Did I just corrupt the drive beyond recovery?

help please

see attachment screenshot of what Gparted reports that it is unrecognized disk

---

### Post by Yellow Pasque on 2015-02-10
You can create a new partition table under the 'Device' menu in gparted. Obviously, that will erase any data on the drive.

---

### Post by michael-piziak on 2015-02-10
> **Temüjin said:**
> You can create a new partition table under the 'Device' menu in gparted. Obviously, that will erase any data on the drive.

Yes I attempted that.  I partitioned (formatted) it as ms-dos.   The operating system still will not recognize the drive when inserted.    

Still however, gparted and disk utility can see and format the card - ?

???

I'm glad I didn't do this to my 128 gig flash drive.

Additional info:  I formatted this 8 gig card as "bsd," and that is when it became invisible to Ubuntu 12.04 lts

---

### Post by Yellow Pasque on 2015-02-10
Okay, so after you created new partition table, did you create a new partition? Otherwise, it's not going to see/recognize volumes that don't exist.

Can you show output for fdisk? (just the part for the flash drive; don't care about your disk)
```
sudo fdisk -l
```

---

### Post by michael-piziak on 2015-02-10
using gparted:

I went to "device" and created a new partition table.

then I went to "partition" and selected "new"

It appears to be hanging - says "1 operation pending"

Also, the sudo command reports:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo fdisk -l
[sudo] password for michael: 


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005ef36


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480174079   240086016   83  Linux
/dev/sda2       480176126   488396799     4110337    5  Extended
/dev/sda5       480176128   488396799     4110336   82  Linux swap / Solaris


Disk /dev/sdb: 7816 MB, 7816085504 bytes
241 heads, 62 sectors/track, 1021 cylinders, total 15265792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f057c


   Device Boot      Start         End      Blocks   Id  System
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by tea for one on 2015-02-10
> **michael-piziak said:**
> using gparted:


It appears to be hanging - says "1 operation pending"


In your screenshot, it appears that you have requested the formation of an Ext2 partition but you have not completed the format.

In Gparted, you have to click on the green tick to complete the procedure.

Make sure that you have backed up important data.

Good luck

---

### Post by Yellow Pasque on 2015-02-10
> It appears to be hanging - says "1 operation pending"

You have to apply your changes (see the green checkmark icon?).

---

### Post by michael-piziak on 2015-02-10
Thank you thank you thank you !   
I clicked the green tick and it brought it back alive again!

Marking this thread as solved!

Thanks again !

---

