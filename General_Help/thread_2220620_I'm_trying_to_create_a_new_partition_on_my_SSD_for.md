---
title: "I'm trying to create a new partition on my SSD for Windows"
date: 2014-04-28
forum: General Help
---

### Post by josmei97 on 2014-04-28
I want to dual boot Windows and Ubuntu on my SSD, /dev/sdb1

When I first installed Ubuntu it used the whole SSD as a partition, even though most of it isn't being used. How do I unmount it and create a new partition to install windows on?

---

### Post by oldfred on 2014-04-28
Use gparted & shrink Ubuntu partition. 
Is drive MBR(msdos) partitioned? If UEFI/gpt totally different instructions required.

You have to use gparted from a live installer or gparted liveCD or parted magic liveCD. Little key symbols mean a partition is mounted and you cannot work on mounted partitions.

Create a primary partition with the boot flag formatted NTFS. Then Windows should find that partition and let you install to it. It will overwrite the grub boot loader in the MBR, so have Ubuntu live installer or Boot-Repair handy to restore grub to MBR. Be sure to change BIOS boot order to boot from SSD, or Windows will install a boot partition on the drive set to boot in BIOS. And it will just overwrite whatever is there if not a NTFS partition with boot flag.

---

### Post by josmei97 on 2014-04-28
> **oldfred said:**
> Use gparted & shrink Ubuntu partition. 
Is drive MBR(msdos) partitioned? If UEFI/gpt totally different instructions required.

You have to use gparted from a live installer or gparted liveCD or parted magic liveCD. Little key symbols mean a partition is mounted and you cannot work on mounted partitions.

Create a primary partition with the boot flag formatted NTFS. Then Windows should find that partition and let you install to it. It will overwrite the grub boot loader in the MBR, so have Ubuntu live installer or Boot-Repair handy to restore grub to MBR. Be sure to change BIOS boot order to boot from SSD, or Windows will install a boot partition on the drive set to boot in BIOS. And it will just overwrite whatever is there if not a NTFS partition with boot flag.
It looks like I'm going to have to use gparted from a live cd, but I don't have a cd to burn it onto right now, if I install windows on my HDD can I reinstall it on the SSD once I create a partition?

---

### Post by oldfred on 2014-04-28
Install another copy of Ubuntu on HDD. I like to have an install on every drive anyway. Good for testing next version or experimenting with settings. And is then a backup way to boot. Does not have  to be a large partition.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

Windows is not so easy to move and is particular about many things.

---

