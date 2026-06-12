---
title: "Testdisk Stuck"
date: 2008-07-04
forum: General Help
---

### Post by Keller on 2008-07-04
Hi,
I am having a little bit of trouble with my Dual Boot Windows/Ubuntu. I've been trying to fix this myself, but I think I may need some pointers. My immediate problem: Testdisk is stuck on "Checking Current Partition Structure" and won't do a thing.

Here is why I'm using Testdisk:
I had built a new computer and wanted to run it, but did not have a windows disk, so I installed Ubuntu (First time linux). I later borrowed a windows disk, and installed that on the NTFS space I had allocated for it, however, I was not aware that I did not have a valid license, so I only used it in trial mode for 30 days. Then, after it had expired, I bought my own XP (reason is that some of the programs I want to use don't run under wine). However, I was not able to activate it, so I cleared the NTFS partition in Gparted to unallocated, re-formated it with the Windows installer as NTFS and everything went fine. I installed a game (the sims II) from Windows on the shared ext3 partition, and at some point the game crashed while trying to safe (the safe files are default stored to the NTFS partition), the computer crashes completely, restarts, and then gives an error message "Disk Read Error" I had not re-activated grub, so I threw in my Ubuntu Life CD and started to get stuck. I was trying to see if mounting/unmounting drives would help, so I unmounted my ext3 partition, but gparted crashed in the process. Last time I started it it recognized the partition, but did not find a disk label for it. Now, neither Gparted nor TestDisk ever finish scanning my Harddrive. Help?

So I need to:
1. Get my ext3 file partition back up
2. Re-activate Grubb
3. Fix my NTFS partition to boot again

preferably in that order and order of importance. Any advice would be great.
One thing I have been having trouble with concerning re-activating grub: How do you find out which partition it is supposed to be reactivated from? I found the following code:
> sudo grub
> root (hd0,0)
> setup (hd0)
> exit
well, my hd0,0 is MIA right now, and I'm not so sure that is the right one. How do I find out where grub really is for me?

oh, and my recovery disk is Ubuntu 7.10

Thanks a ton and a cup of Ubuntu

---

