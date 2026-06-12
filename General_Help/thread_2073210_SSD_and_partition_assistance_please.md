---
title: "SSD and partition assistance please"
date: 2012-10-19
forum: General Help
---

### Post by np123 on 2012-10-19
Hi there. I just picked up a new SSD drive and im swapping oout my old HDD for this one.
 
I plan to install Ubuntu 12.10 on there, and I dont need much of a techinical setup, so i plan to just have something like:
 
/root 20GB
/home rest of drive GB
 
Is it correct that I shouldnt use swap on an SSD drive?
 
What tweaks should i do - i plan on using discard and noatime anyway?
 
Many thanks

---

### Post by LiamOS on 2012-10-19
Swap is generally a good idea. If you'll have two drives, one mechanical, put swap on that. Otherwise I'd put a bit of swap on the SSD and turn swappiness down really low.

20GB for / seems reasonable. On this box, I've a Gentoo installation with Libreoffice, Firefox, and XFCE all under 10GB including the source tarballs, so 20 should suffice for Ubuntu with whatever software you add.


Some filesystems have SSD optimisations, such as xfs and btrfs(Actually just turns off rotating optimisations :P), and you should probably use those if your filesystem does that. As far as those two go, xfs is probably a better bet unless you specifically want a COW filesystem. The only problems I've had with xfs are that you can't shrink a partition(can be annoying sometimes), and that it's not very space efficient on really small partitions like <1GB.
Other than that, noatime and discard should serve you well.

---

### Post by np123 on 2012-10-19
Thanks for that, great explanation.
 
One thing I am stuck on though is whether I should add swap or not?
 
I have 4GB or Ram on a 64Bit system. I wont hibernate, I always turn on and off. I dont edit videos (but might who knows).
 
Should I use swap or not. 
 
And if yes, should I use a swap file or a partition? I only have a SSD drive, no mechanical drive.

---

### Post by 2F4U on 2012-10-19
If you don't have swap and your RAM begins to fill, thing will become really slow. So in my opinion it is always a  good idea to have a swap partition. With respect to the SSD, if the swap partition isn't used it won't harm the SSD. So, my recommendation is to create a swap partition and make it at least as large as the installed RAM.

---

### Post by MrsUser on 2012-10-19
When RAM sizes were still low (512MB etc) the general rule was swap to have double the RAM size. Now today, with huge RAM size, this isn't really a general rule anymore. Anything with RAM 4GB+ doesn't need double the swap. 1 x the RAM size is enough. In your case you're on the safe side with 4GB swap (but if you do a lot with virtualization machines, such as with VirtualBox stuff, then choose more). Make it a separate partition.

I recommend the following (in order):

swap 4GB
root 20GB
 /home

If you put swap at the beginning, there is the advantage that you can always still change the sizes of the other partitions afterwards without any big hassle, especially on a re-install.

20GB for root is reasonable, although my Ubuntu 12.04 64bit with all my needed software installed is under 6GB. My root partition is 25GB. But next time I'd go for 20GB too.

---

### Post by np123 on 2012-10-19
Thanks very much people. I knew i was over thinking it. Too many scare stories floating around.
 
I'm going to put a swap partition on there. I'm also going to upgrade my RAM to 8GB at some point as i do use virtual machines quite a bit.
 
On my SSD:
 
Swap 4GB
/Root 20GB
/Home - Rest
 
Should be fine. 
 
Although, i guess swap can go at any point of the SSD now given its not a spinning drive.
 
Maybe easier to go:
 
/Root
/Home
Swap

---

### Post by 2F4U on 2012-10-19
> Although, i guess swap can go at any point of the SSD now given its not a spinning drive.
 

For a SSD, this assumption is correct.

---

### Post by oldfred on 2012-10-19
Lots of detail on SSD.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Some info on file systems:

Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox ssd
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

Another choice on swap. I still suggest swap partition but put it on a rotating drive. Herman uses the dynamic swap 

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
[http://pqxx.org/development/swapspace/](http://pqxx.org/development/swapspace/)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

