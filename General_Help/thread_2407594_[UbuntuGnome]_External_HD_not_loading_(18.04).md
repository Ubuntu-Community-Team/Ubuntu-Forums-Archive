---
title: "[UbuntuGnome] External HD not loading (18.04)"
date: 2018-12-06
forum: General Help
---

### Post by Robbyx on 2018-12-06
Mother Board: ASROCK FM2A88X Extreme6+ 
Processor AMD-a10 -7800 Radeon R7
OS UbuntuGnome 18.04LTS
RAM 16gb

Yesterday morning, I found that the Samsung ext HD was not appearing as a device and there were error messages to the effect "no such file or directory... non existent device". 

As the external drive is allocated to SDB, I tried "sudo fsck -ycfTV /dev/sdb2" also on sdb3 and sdb4. Those devices were not being recognised as present.

A restart caused the system to report that there was a start job running  on each of the   sdb partitions. I tried to run fsck from the root  when starting but the system had not loaded the sdb drive. 

I have tried to boot off the live CD. The sdb drive was not loaded and so no diagnostics could be run at that point. 

I have just  been able to get back into the sdb drive by unplugging both the data and the power cable, rebooting into the system and then plugging back the cables. No files  appear to be missing from the sdb drive. I have run "sudo fsck -ycfTV /dev/sdb2" and there were no errors.

I have just hashed out the sdb drive's partitions  from the fstab file and am hoping that if I have to restart the system the usb drive will be picked up and loaded without the help of the fstab settings. 

What further tests should I run?

At the moment I am running "sudo fsck -ycfTV /dev/sdb3". There are no errors so far.

I have looked at the smart disk report: 

Last selftest completed successfully
Self Assessment: Threshold not exceeded
Overall ass't: Disk is ok, 88 bad sectors. From past error reports, I think the bad sectors are sdb1 partition  which is FAT(32-bit)

> sudo fsck -ycfTV /dev/sdb1
[/sbin/fsck.vfat (1) -- /dev/sdb1] fsck.vfat -ycf /dev/sdb1 
CP0: Invalid argument
Trying to set fallback DOS codepage 437
fsck.fat 4.1 (2017-01-24)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:00/01
  Not automatically fixing this.
Performing changes.
/dev/sdb1: 3 files, 2050/76646 clusters
robins@robins-desktop:~$ 


I am hoping that I can be helped over this problem as set out in the posting. It is now 6 hours since I posted the original message and I am anxiously hoping for a quick reply so that disaster can be avoided for me.

---

### Post by Autodave on 2018-12-06
You have to realize that everyone here is a volunteer: no paid positions. And the person that might be able to help you could be anywhere in the world.

88 bad sectors is not good: you may have a HD going out.  Running a disc check can tell you that you definitely have a bad disc, but it cannot ever tell you that the disc is good.  Until someone else can offer you better advice, that's my opinion: the HD is going bad.

---

