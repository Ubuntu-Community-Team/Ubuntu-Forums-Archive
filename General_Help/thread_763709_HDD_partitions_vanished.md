---
title: "HDD partitions vanished"
date: 2008-04-23
forum: General Help
---

### Post by Luisv on 2008-04-23
I was installing Linux on my external HDD... it went wrong, and I entered the manual mode to do the partitions I saw that one was wrong and I clicked on "undo the changes of the partitions". Then _all_ the partitions were undone, my internal HDD's too.I had Windows XP, and im now writing this with the live CD of Linux.Are there any ways of restoring all files or partitions?
Help please.:(

Sorry for my bad english;)

---

### Post by mozetti on 2008-04-23
Please post the output of this command:```
fdisk -l /dev/hda
```

If you have SATA disks, use "sda" instead of "hda"

---

### Post by Luisv on 2008-04-23
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfce28df

   Device Boot      Start         End      Blocks   Id  System

---

### Post by markjensen on 2008-04-23
If you just had a simple single filesystem (partition) missing, I would just re-create it.  But you likely had one or more NTFS partitions, one or more Linux ext3, plus a swap.

I would recommend using a tool called RIP (Recovery is Possible)
[http://en.wikipedia.org/wiki/Recovery_Is_Possible](http://en.wikipedia.org/wiki/Recovery_Is_Possible)

It is primarily console-driven textbased apps, but one of them looks at your hard drive's data area, and is able to ascertain with good accuracy (in the single test I have done with it) what your partition table **should be** to make things right again.

Best of luck!

---

### Post by ryanhaigh on 2008-04-23
I believe testdisk, which can be installed into the running livecd session also has this functionality, although I have not used it myself it is often mentioned on these forums when dealing with issues such as this.

---

### Post by Luisv on 2008-04-23
Thanks!I thought I would loose all my HDD's Data. I'm very grateful to you for your help. I'll try it out.:)

---

### Post by markjensen on 2008-04-23
"testdisk" is the app included with RIP that I used.   I did not know it was included on the Ubuntu CD as well.   Good to know!  :D

---

### Post by ryanhaigh on 2008-04-23
I don't think its installed by default on the ubuntu livecd but its only a sudo apt-get install testdisk away.

---

