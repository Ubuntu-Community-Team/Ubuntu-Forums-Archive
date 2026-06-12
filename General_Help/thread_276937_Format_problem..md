---
title: "Format problem."
date: 2006-10-13
forum: General Help
---

### Post by Freddy on 2006-10-13
Hi all. Want to format a 160gb partition to fat32, either through qtparted or with the help from a console.

I tried to install qtparted but it only found my "hde" drive and not my "hdb" that the partiotion is on. So I went to cfdisk but it refused to write the partition table if I didn't make one partition bootable. which I don't want to do.

Can someone pls help me to find all my drives in qtparted or guide me through cfdisk.

The drive that I want to use is "hdb" and the setup on that will be.

hdb1 160gb fat32
hdb2 8gb ext3
hdb3 25gb ext3

The other 2 partitions is done but Kubuntus install didn't make my fat32 lbs compatible so I need to fix that. Thx for any help I can get. /// Freddan

---

### Post by Freddy on 2006-10-13
Bump

---

### Post by Peepsalot on 2006-10-13
I highly recommend the gparted livecd for partitioning.  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I used it recently on my edgy install, and it worked without any problems.  The gparted program included on the Ubuntu cd's however could not correctly recognize all my drives.

Also, if you are using your fat32 partition simply as a share between windows and linux on a dual boot, then take a look at [http://www.fs-driver.org/](http://www.fs-driver.org/)
It lets you read and write ext2(or3) partitions in windows.  I can't say I've used it, but I plan on giving it a try pretty soon.

If you need the partition for a windows install however, then that won't work.

---

### Post by Freddy on 2006-10-13
Thx a bunch. I will try that fs-driver for win. I've been using a fat32 shared partition for ages, but now when I have a need for a larger shared drive and lba seem to mess thing up, that driver could be the easy solution.

---

