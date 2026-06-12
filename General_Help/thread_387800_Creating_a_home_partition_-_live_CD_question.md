---
title: "Creating a home partition - live CD question"
date: 2007-03-18
forum: General Help
---

### Post by OrangeCrate on 2007-03-18
I'm going to add a home partition using these instructions:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I upgraded to Edgy from Dapper, and my live CD is Dapper from shipit.

Do I need a new Edgy live CD to do this, or will my existing Dapper CD be O.K. to use?

---

### Post by raja on 2007-03-18
Any live cd with the gparted should do.

---

### Post by OrangeCrate on 2007-03-18
Thanks. :)

---

### Post by OrangeCrate on 2007-03-19
From what I've seen searching the forum, the home partition numbers I see are pretty big. I have an older computer with a 60 gig hard drive, and only 384 meg of RAM.

Here's how it's currently partitioned:

sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60060155904 bytes
240 heads, 63 sectors/track, 7758 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         677     5118088+   b  W95 FAT32
/dev/hda2   *         678        4946    32273640    7  HPFS/NTFS
/dev/hda3            4947        7639    20359080   83  Linux
/dev/hda4            7640        7758      899640    5  Extended
/dev/hda5            7640        7758      899608+  82  Linux swap / Solaris

I would take space from the NTFS partition to create the home partition, as I seldom use Windows. Could someone be kind enough to suggest a size?

---

### Post by buuntuu! on 2007-03-19
depends on your needs!
for the root partition 5 gig should be more than enough, the rest of it can go to /home
before resizing NTFS make sure that it is defragmented. i recommend [jkdefrag,]("http://www.kessels.com/JkDefrag/") works better than xps default defragger.
let it run twice, then you are ready to go.
backup though, althoug i never had any trouble it's good to be on the safe side ;)
have fun

edit: 
you could access /home from both OS using ext3 fileformat and installing a [driver]("http://www.fs-driver.org/") in window$ which gives it read/write-access to your /home
that way you could get your personal data off ntfs and leave just enough room for window$. make it about 1 gig bigger than the used space, just in case you want to install something...

---

### Post by OrangeCrate on 2007-03-19
O.K  thanks, I think I understand that enough to give it a try. I appreciate your help.

---

