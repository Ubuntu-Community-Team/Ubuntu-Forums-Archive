---
title: "Rut Row....repartitioning drive &amp; moving /home disaster !!!!"
date: 2022-02-13
forum: General Help
---

### Post by ozark_hillbilly on 2022-02-13
Okay, I decided to go in and move things around on my 250GB hard drive to increase swapfile area
and create a separate /home partition.

Using this guide:

How to Create a Separate Home Partition After Installing Ubuntu

[https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

If you look at my screenshots you see sda5 is a little wonky. The issue seems to be I did not successfully
move the /home data out of sda5 and into sda6. Sda5 is now overflowing...lol

As a result the operating system stops loading Ubuntu at a certain point before loading the Desktop, etc.

Since partitioning is completed can I somehow move the /home folder with Nautilus or do I need to attempt it 
with terminal mode? I do not want to do another fresh install as I have the partitioning as I now wanted it.

The screenshots show gPARTED and Disks info. Pay particular attention to the info on sda5.

```

buntu@ubuntu:/$ sudo fdisk -l /dev/sda
Disk /dev/sda: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: WDC WD2500AAKS-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa5101b40

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048   1050623   1048576   512M  b W95 FAT32
/dev/sda2        1050624   2101247   1050624   513M  b W95 FAT32
/dev/sda3        2103294 488396799 486293506 231.9G  5 Extended
/dev/sda5        2103296  66785279  64681984  30.9G 83 Linux
/dev/sda6       66787328 150673407  83886080    40G 83 Linux


```

Is this a hopeless situation or can I resurrect this situation w/o too much grief?

thanks as always....

---

### Post by TheFu on 2022-02-13
**lsblk -e 7 -o name,size,type,fstype,mountpoint** output please. 

At first look, there are some things I'd do different.
a) GPT, not MSDOS partition table. GPT is better for many, many, reasons.
b) GPT doesn't use extended partitions, so things are easier. GPT only has primary partitions, so they don't all have to fit inside any extended partition. GPT allows over 100 primary partitions, so the 4 primary partition limit that MSDOS partition tables have aren't a problem ---- ever.
c) Only 1 FAT32 partition is needed. Why 2?  I honestly am confused.  FAT32 really shouldn't be used anymore, anywhere, except for the EFI boot needs where it is mandatory (by the EFI standards). It should not be used anywhere else, unless there is a hardware limitation ... like old point-n-shoot cameras.  On either SSD or HDD, use ext4 unless you have a very good reason to use some other file system. The /boot/ partition for Linux cannot be a non-native file system.
d) Where's the swap?  All Linux needs "some" swap.  For a desktop, 4.1G is my recommendation. Not too large, but still big enough that out of memory issues won't happen without you feeling the system getting much slower first.  For a server where the workload is extremely well-understood and sufficient RAM exists, 1G of swap is recommended. There are some performance enhancements that Linux can do, but only if there is "some" swap.  For years, I ensured my Linux servers all had more RAM than needed. I've been adding some swap to them recently to gain performance.  There's an internal kernel thing that enables some stuff if there is swap which aids performance. It actually never gets used more than just a few MB, but having "some" matters.

The good news is that you have plenty of unallocated space in the extended partition.  Might be smart to ensure there is 50G unallocated between both Linux partitions so that if future growth is needed for the first 1 (sda5), then you can expand in seconds "to the right" using gparted.  If both partitions are right next to each other, then you'll need to move 1 to make room. Moving a partition is hard work and can take hours.  Extending a partition left is also very hard work.  Extending a partition to the right is easy, provided there is empty space available.

But if you agree with my statements above, I'd start over, ensure that GPT gets used and do the other things.  For a desktop Ubuntu, 30G might be too small thanks to snap packages and the installer may create a swapfile (rather than a swap partition - eeeew). I'm not a fan of swapfiles.  On an SSD, it probably doesn't matter. Canonical engineering often makes choices driven by outside reason, not technical reasons. I think the swapfile is 1 of those examples. If you use GPT, then having a swap partition just doesn't matter, since there isn't a 4 partition limitation.


IMHO.

---

### Post by Impavidus on 2022-02-14
Disks clearly gives false information. It reports that usage of sda5 is negative. It could be confused by recent changes done by gparted. Ignore it.

Use your live disk. Mount both sda5 (I assume that's the root partition of your installed system) and sda6 (that would be the /home partition of your installed system), for example on /mnt/root and /mnt/home. Copy the contents of /home on the root partition to the root of the /home partition, making sure that all permissions and ownership are preserved. It's best to use rsync for that; Nautilus may not be smart enough to preserve ownership and permissions. Verify that the copy went well, verify that /etc/fstab on the root partition has the right configuration to mount the /home partition and delete the contents of /home on your root partition, so that /home is an empty directory.

But I agree with TheFu. Some things are not optimal. Why use relatively tight partitions for root and /home when most of the drive is still unallocated? Unless you intend to make some more partitions there. I see you have a second hard drive and from a different thread I remember there was some swap space on that. I don't know what else that second drive is used for.

---

