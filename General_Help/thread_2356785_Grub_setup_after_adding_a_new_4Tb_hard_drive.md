---
title: "Grub setup after adding a new 4Tb hard drive"
date: 2017-03-27
forum: General Help
---

### Post by pelennor on 2017-03-27
Hi all,

I'm having some issues trying to get my Kubuntu 16.10 system to reconfigure grub and boot after adding a 4TB hard drive.

Prior to adding the drive my layout was as follows:

sda: 2TB drive with bootable  partition (LVM partition)
sdb: 120G SSD with root partition and home partition
sdc: 2TB drive with LVM partitions

Note all boot sectors on these are MBR.

Since the motherboard only has two SATA3 slots, and the former "sda" is a slower drive, I reconfigured as follows:

sda: 4TB new drive, GPT boot record 
sdb: 120G SSD with root partition and home partition
sdc: 2TB drive with LVM partitions
sdd: 2TB drive (former sda)

Despite using boot-repair to install grub to sdb, and changing the hard drive priority in BIOS to sdb first , booting from hard drive doesn't work (doesn't even get to a grub prompt, slow dots then blank screen)

Any ideas what could be wrong, what to look at, or how to fix it?

---

### Post by ajgreeny on 2017-03-27
It will be helpful to those who are more able than I am if you run the Boot-Info script from Boot-repair again and just post the results of the script with the details of your system; this will be best done by copying the **pastebin** link you get.

However, for booting Linux in legacy mode (MBR) on a GPT drive you need a BIOS-GRUB-partition without any filesystem and flagged as BIOS_GRUB which I do not see in your simple list of partitions.
This is a small space of only 1MB, unformatted to any filesystem; just left unallocated, and most easily done using gparted from a live system. Right click in that space to add the BIOS_GRUB flag.

---

### Post by pelennor on 2017-03-27
OK the pastebin link for the current config is [http://paste2.org/gwcOWw2z](http://paste2.org/gwcOWw2z)

Even though sda is GPT, I'm attempting to both have the grub boot loader and the root partition on sdb .. I'm assuming in that case no BIOS-GRUB required since sdb is still MBR formatted...

---

### Post by oldfred on 2017-03-27
You should be able to boot from sdb.
Not seeing a lot of issues, but your fstab mounts a partition with label LABEL=chris-bu, but blkid, does not show that label?

Also with the new very large TB drives, I suggest including the bios_grub partition, so if in future you want to add an operating system you can. 
And if any chance drive will later be used in a newer UEFI system also include the ESP - efi system partition which should be first or at least near beginning of drive. Both are not large, so no real wasted space and makes reconfigure easier later if desired.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive. 
And I have only partitioned new or reformatted drives with gpt and both bios_grub & ESP since about 2011, including all larger flash drives.

---

