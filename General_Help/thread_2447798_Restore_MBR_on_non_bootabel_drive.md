---
title: "Restore MBR on non bootabel drive"
date: 2020-07-26
forum: General Help
---

### Post by seppmuc on 2020-07-26
Hello,
I have an external Harddrive with a defekt MBR which I by myself damaged while installing a new operation system.

Here is the logfile.

[http://paste.ubuntu.com/p/3ZgbFkgZmw/](http://paste.ubuntu.com/p/3ZgbFkgZmw/)


Can somebody help me restore the boot-table of sdc5?

Thx a lot.

Regards,
Martin

---

### Post by pbear42 on 2020-07-26
It's not clear what you're trying to accomplish.  If it's repairing the boot loader, would be simpler to reinstall Grub.  If you've lost the partition table, that's a bigger problem.

In any event, you might find this article useful: [https://www.linuxjournal.com/article/10385](https://www.linuxjournal.com/article/10385)

---

### Post by oldfred on 2020-07-26
Do not run any auto-fix from Boot-Repair.
Only use its advanced mode and select one install & install grub for that install to the same drive.

But you have old & very old installs.
Your 16.04 is still current until April 2021. But then you need to have upgraded.
Since several drives you may want to install 18.04 or 20.04 or both into different drives, soon.

You do not install grub to a partition - PBR, just to MBR. So do not install to sdc5.
And sdc5 is NTFS, you do not install grub ever to NTFS partitions as Windows has essential boot info in the NTFS PBR.
And Windows cannot be directly booted from a logical partition. Windows only boots from a primary NTFS formatted partition with the boot flag and its boot files. You can then have the main part in a logical partition but that is not normal nor recommended.

You show no Windows boot files, but it looks like older obsolete versions.
Time to upgrade?

---

### Post by seppmuc on 2020-07-27
Hello,
thx for the support. I do not need to boot from the sd5 NTFS harddisk. The disc was never a bootable harddisc, only a data storage. 
I just would like to access the data of the disk with the broken pbr.

And yes, the harddisc was last running under windows, not under linux. 
I just thought, I could repair the broken pbr with linux. 
I read that you need to maniuplate hexadezimal numbers anywhere...

---

### Post by oldfred on 2020-07-27
If newer Windows, it turns fast start up on which sets a hibernation flag. The hibernation flag will prevent the Linux NTFS driver from mounting the partition read/write to prevent damage.
Also Windows needs chkdsk or defrag which only can be done from Windows. So unless you have Windows or at least a Windows repair flash drive, do not use NTFS.

You may be able to manually mount read only to copy your data.

External drive, use safe eject or try manual mount read only with recover
[https://superuser.com/questions/1231582/hdd-with-windows-boot-locked-because-of-hibernation-flag](https://superuser.com/questions/1231582/hdd-with-windows-boot-locked-because-of-hibernation-flag)

Force mount, read only (ro), change example with sda3 to your correct NTFS partition:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

---

