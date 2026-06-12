---
title: "reorganizing partitioning scheme post-install"
date: 2007-10-12
forum: General Help
---

### Post by zaprenki on 2007-10-12
Hi there...
Before I begin, I would like to apologize for the relatively big post, I just want to be as accurate and descriptive as possible.
I 've installed Ubuntu 7.04 and now I'm spending happy time playing with it :)
The initial hard disk setup was a 200 GB hard drive with WinXP Pro installed. I used Partition Magic and created 2 extra partitions for Ubuntu, a 1 GB swap partition and a 3 GB ext3 partition where the root filesystem was installed.
After a successful install I realised that the 3 GB partition was not enough, as 2.5 GB were already occupied by the system, leaving me with only 500 MB of free space. So I used Partition Magic once again and extracted 3 more GB from the Win XP partition, creating a fourth partition.
My original purpose was to join the two 3 GB partitions to a 6 GB one, where the root filesystem could be mounted. I searched Ubuntuforums thoroughly but couldn't find a way to do this. Booting from Ubuntu LiveCD and using the partition manager does not allow me to resize the existing ext3 partition, neither does Partition Magic. So I followed another solution that I found, and moved the /home directory to the newly created 3 GB partition.
The problem is that even this solution is practical for keeping my settings and files after new installations, it doesn't help much with free space issues, as the root filesystem still has only 500-600 MB free, and program installations write their files in / and not in /home. So I'm stuck with an almost full / partition and an almost empty /home partition with not much use for it.
Could anyone suggest a more viable solution on how to reconfigure my disk space and partitions? I would like to grow the / partition to 5-6 GB while /home partition could be left with 1-2 GB. The WinXP partition has about 45 GB free and I can use Partition Magic to create as free space as needed.

---

### Post by Sef on 2007-10-12
> I used Partition Magic

Partition Magic and Linux do not always get along.   Instead use [GParted,]("http://gparted.sourceforge.net") it can resize ext3 partitions.

---

### Post by zaprenki on 2007-10-12
Well, I only used Partition Magic to extract some free space from the WinXP partition, as it works better with NTFS. When the installation was complete, I installed Gparted and tried to use it. When I ran it from my system, it wouldn't allow me to resize either partition (the menu option is grayed out). I guess this is because both / and /home partitions are mounted and can't be unmounted. When I ran Gparted from LiveCD system, again it wouldn't allow me to resize any ext3 partition.
So no luck here...:(

---

