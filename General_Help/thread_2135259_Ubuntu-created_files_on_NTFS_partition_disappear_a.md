---
title: "Ubuntu-created files on NTFS partition disappear after booting Windows 7"
date: 2013-04-13
forum: General Help
---

### Post by avril22 on 2013-04-13
Hello.

I just got a new computer (Lenovo Thinkpad T430) and am dual-booting Ubuntu 12.04 with Windows 7 (both 64-bit), with a shared NTFS partition for storage between them.  Both operating systems can see the partition, and can read and write files on it.  However, if I *create* files on the partition from Ubuntu, these files disappear once I boot into Windows.  I would like to figure out how to prevent this.  I have found many posts on the internet about people who have had similar problems, but none of them have exactly the same symptoms as I'm seeing.

Details:

- When I say the files "disappear", I mean, they don't show up in a file browser (or ls) from either operating system, ever again (I have enabled show-hidden-files on both OSes).  But I think they are still *there*, because both operating systems show the partition as having about 6 GB used, which is the amount of space the disappeared files took up, and visibly there are pretty much no files on the partition.

- From Windows I can create files on the partition, and from Ubuntu I can modify the files that were created from Windows, and those changes don't disappear.

- If I create files on the partition from Ubuntu, then turn off the computer and then turn it back on and boot back into Ubuntu, the files are still there, they only disappear once I start Windows.

- I'm pretty sure this is not related to "hibernating", because it happens even if I turn the computer off completely in between operating systems.  I have never intentionally told the computer to hibernate from either operating system.

- The fstab entry in Ubuntu for the NTFS partition is
UUID=32D5B382578D1B41  /storage  ntfs-3g  rw,suid,noexec,async  0  2

- (not sure if this is relevant but)  The arrangement of partitions on the disk is
+ [primary partition] some small Windows system partition that I didn't mess with
+ [primary partition] main Windows partition
+ [primary partition] shared NTFS partition
+ [logical partition] Ubuntu partition (ext4)
+ [logical partition] swap partition for Ubuntu
The GRUB2 bootloader is installed in the Ubuntu partition (not in the MBR) (because the internet said that putting it in the MBR could mess things up).

So, it seems like what must be happening is that whenever Windows starts up, it's looking at the NTFS partition and being like "hey what are those things, I've never seen those before, they must not be real files, hey filesystem don't treat those as files".  I want to make it not do that.  Any advice would be appreciated.

Thanks!


P.S.  I'm not sure which "prefix" I'm supposed to put in the title of this post - at least three of them seem applicable ([ubuntu], [64 bit], and [other_os]), but I can only select one, and selecting any one of them seems misleading, since it's possible that this problem is not actually specific to any of them.

---

