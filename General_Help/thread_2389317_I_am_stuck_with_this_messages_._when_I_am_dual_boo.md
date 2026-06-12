---
title: "I am stuck with this messages . when I am dual booting windows along side with ubuntu"
date: 2018-04-15
forum: General Help
---

### Post by gopal29 on 2018-04-15
HI there I am gopal..!


I have installed windows 10 os on my laptop. I want Ubuntu along side with windows 10 . so I am trying to dual booting my system in the middle of the process 

I stuck with message as "  /dev/sdb

DO YOU WANT THE INSTALLER TO TRY TO UNMOUNT THE PARTITIONS ON THIS DISKS BEFORE CONTINUING? IF YOU LEAVE THEM MOUNTED YOU WILL NOT BE ABLE TO CREATE DELETE OR RESIZE PARTITION ON THESE DISKS BUT YOU MAY BE  ABLE TO INSTALL TO EXISTING PARTITION THERE

SAY YES/NO"

what is this problem for the above message  and  how to solve this problem 

how to create partition on hard drive .preloaded windows 10 os  on hard drive
and I am unable to create partition for Ubuntu ?
please help me

---

### Post by TheFu on 2018-04-15
Windows doesn't close open file systems at reboot.  That can lock partitions.  Inside Windows, disable fastboot. Win10 changed the name, I think. [https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/](https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/)

The installer is protecting you. Good to ask BEFORE doing anything. Very smart. Always, be very careful using "force" - very careful. Unix systems will let you do things that might not be good for you. That is a philosophical difference from most other popular OSes.

---

### Post by oldfred on 2018-04-15
While I think your issue is exactly what TheFu has suggested as the issue, I do get that same error on my system which is Linux only.


But it is because I use grub to directly boot an ISO on one drive for install to another hard drive.
And then it arbitrarily mounts the ISO to /dev/sda3 which is already another partition. My data in sda3 does not seem to be damaged.
I did find it better to use a toram boot parameter and then unmount (umount) the ISO device.

 Unable to umount isodevice unmount ISO
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216)
sudo umount -l -r -f /isodevice

---

### Post by yancek on 2018-04-15
I've seen that message on pretty much any recent install of Ubuntu or derivatives.  The question is, what is sdb?  The message is clear.  If you want to modify partitions on sdb, say yes, if not say no.
If you are installling Ubuntu to the same physical hard drive as windows, did you use Disk management on windows to shrink the largest windows partition to leave unallocated space on which to install Ubuntu?   Did you install windows 10 UEFI?  If so, do the same with Ubuntu, see the documentation page below.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by TheFu on 2018-04-15
slightly related... 

Something that might not be clear and we haven't said is that whole disk drives have devices on Unix/Linux systems based on the order they are found by the OS and BIOS.
/dev/sda is the first SATA/SCSI storage device found. This is usually the main OS HDD in a system.
/dev/sdb is the 2nd SATA/SCSI storage device found.  Often, this is a flash drive or 2nd HDD in a system.
/dev/sdc ... sdz are the next SATA/SCSI devices found.

Often, the device order a, b, c, is tied to the SATA port used on a motherboard.  Sometimes, a builder might connect a DVD SATA cable to the sda SATA port on the motherboard, so sdb might be the main HDD.

New-fangled SSDs that are connected by PCIe cards might have different driver names like /dev/nvme... Don't quote me. I don't have any of those.

Older systems have /dev/hba because IDE interfaces use "hb" drivers.

Next, it is important to know that partitions on each HDD get a number and a new device, but that device name is clearly related to the HDD device name.
/dev/sda1 is the first partition on the HDD with sda name.
/dev/sda2 is the 2nd partition on the HDD with sda name.
For GPT partition tables, the partition numbers are sequential, based on the order created.  1,2,3,4 ... 120 ... to whatever the limit is for partitions.  This would apply to hda1 ... hda50 ... or nvme1 to nvme100 as well.

In non-desktop systems, lots and lots of storage can be connected. Because of purely timing issues at boot, than means the device names can change from boot to boot, so labels, device paths and UUIDs can be used to dereference the specific device in the OS.  This is the default for /etc/fstab mounts since around 2006.

But during an installation, it is best to keep track of which storage is connected where and the sizes of the storage.  Often, that is enough to ensure you don't accidentally install/wipe onto the wrong HDD.  If you have a 16G flash drive and a 1TB spinning disk, it should be easy to tell which you want to install into.

---

