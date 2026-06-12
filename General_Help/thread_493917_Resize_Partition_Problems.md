---
title: "Resize Partition Problems"
date: 2007-07-06
forum: General Help
---

### Post by xiaozhu on 2007-07-06
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

I followed this tutorial to dual boot Windows XP Pro and Ubuntu. I came to this page...

[img]http://apcmag.com/system/files/images/xp_ubuntu_07.article-width.jpg[/img]

then it said there was problems with Resizing the Partition and bought me to a page with things like this:```
Prepare partitions page

 Device    Type   Mount point    Format?        Size       Used
/dev/sda
   /dev/sda1  ntfs   /media/sda1     [checkbox]   40015mb    0mb


New partition table     Undo changes to partitions

You need to specify a partition for the root file system (mount point "/") with a minium size of 2GB, and a swap partition of at least 256 mb. You may also set up other partitions if you wish.

```

Then I can't resize my partition and hence I cannot continue installing Ubuntu, anyone can help me over here? Thanks....

---

### Post by dabl on 2007-07-06
Here's a better tutorial: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Some questions:

1. Did you do "disk cleanup" and then "defrag" in Win XP before attempting to re-partition?

2. Does this drive actually have at least 10 - 15GB of free space on it?

I recommend a partitioning scheme like this:

/ = 8GB
/{swap} = 1GB
/home = the rest of your available space


And finally a recommendation.  Download and burn a GParted Live CD from this site: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Use that to do your partitioning (not formatting, unless you want to).  When you have the partitions the way you want, then boot your Ubuntu Alternate Install CD (which I also recommend), and simply use the "guided installation" to set the mount points and format the partitions.

:popcorn:

---

### Post by xiaozhu on 2007-07-06
I found someone to help me, but she told me that it was because I am on a NTFS harddisk and I didn't have Windows Installed(she said, by right there should be 2 partition already, but I only had 1)

Does your method really works?

---

### Post by Cool Surfer on 2007-07-07
> **xiaozhu said:**
> I found someone to help me, but she told me that it was because I am on a NTFS harddisk and I didn't have Windows Installed(she said, by right there should be 2 partition already, but I only had 1)

Does your method really works?

The partition that ubuntu will create from free space will be formatted so it does not matter if your windows use ntfs ot fat system.

---

