---
title: "Boot problems, want to dump dual boot windows &amp; go to Ubuntu only."
date: 2018-04-27
forum: General Help
---

### Post by jiminalaska2 on 2018-04-27
Boot/start problems

I want to, need to, go from dual boot to Ubuntu only without losing programs and data in my Ubuntu environment. Will the following plan work or am I more likely to screw my system up even more!

I'm running Ubuntu 16.04.4 on my Dell Inspiron 6605 tower, mfg 2013,  dual boot with windows 8.
 Early this month (April) when I start/boot the computer I  sometimes get a 'you're in low graphics mode'. Other times she'll start up but after login will note a system error, yes, I've been sending the error reports generated. Also on some startup the wi-fi link is lost and the only way I get it back is to re-start. 

I tried running boot repair but the problem is still there. 

Based on the info in the boot repair report (copy of that info  at the end of this post), It appears windows and sda-1 are screwed up and causing the problem.

As I do not use windows here is what I'm planning to do:

Using Gparted I plan to remove sda-1 and sda-2 both ntfs file systems and sda-1 reserved and flagged as boot (although, as noted in the boot repair report I'm not really booting from there),  if I understand correctly, that should remove windows completely from my hard drive. Then I'll  expand sda-3 (where Ubuntu resides) to fill the disk.

Now, do I need to, and if so how do I, create a new boot partition? 

From the boot repair report:
__________________________
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda1 : Error code 14
mount -r /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda2 : Error code 14
mount -r /dev/sda2 /mnt/boot-sav/sda2
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg
______________________________________

---

### Post by yancek on 2018-04-27
Windows 8 and 10 pre-installed are almost always UEFI so you need to check to see if your system is UEFI.  Booting Ubuntu, you can open a terminal and run this command which will show whether you have an EFI partition.

```
sudo parted -l
``` 

There are numerous reasons the system will start in low graphics mode.  Posting any warning or error messages you get would help.
All the error messages you have posted in regard to your ntfs partitions are either because you left windows 8 hibernated (default and if you turn it off it will some times be turned back on during updates).  Google how to do a full shutdown with windows 8, disable hibernation and turn off fast boot.  You may also need to run chkdsk from windows.  THere really isn't anything Linux which can repair anything more than very minor problems on an ntfs filesystem.  It would be unreasonable to expect Linux/Ubuntu developers to create something like that for a proprietary/commercial OS like windows.

---

### Post by jiminalaska2 on 2018-04-28
> **yancek said:**
> Windows 8 and 10 pre-installed are almost always UEFI so you need to check to see if your system is UEFI.  Booting Ubuntu, you can open a terminal and run this command which will show whether you have an EFI partition.

```
sudo parted -l
``` 

....

Thanks for the info, I ran parted -l and got the following :

Model: ATA WDC WD10EZEX-75Z (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  368MB   367MB   primary   ntfs            boot
 2      368MB   210GB   209GB   primary   ntfs
 3      210GB   1000GB  791GB   extended
 7      210GB   512GB   302GB   logical   ext4
 5      512GB   996GB   484GB   logical   ext4
 6      996GB   1000GB  4159MB  logical   linux-swap(v1)


Originally, and still as far as I know, my Dell (a 2013 model) has BIOS  rather than UEFI.

As I said, I'd be quite satisfied  removing windows and going to a single, rather than dual boot. 

Well the procedure I noted in my first posting do this and if so, do I need to create a new boot partition and how would I go about doing that?

---

### Post by oldfred on 2018-04-28
You have BIOS with MBR partitioning.
Windows only boots in BIOS mode from MBR(msdos).
But if system is from 2013, it may be UEFI hardware. As manufacturers had to install Windows 8 in UEFI mode when it was released in 2012. 

You do not need boot partition. If you have grub in MBR and it boots to grub menu, you can delete the NTFS partitions and system will still work. If you modified fstab to auto mount NTFS, you have to remove that also.

You can use the 200GB as a data partition and/or use 25GB for a test install of another Ubuntu.

---

### Post by jiminalaska2 on 2018-04-28
> **oldfred said:**
> ....

You do not need boot partition. If you have grub in MBR and it boots to grub menu, you can delete the NTFS partitions and system will still work. If you modified fstab to auto mount NTFS, you have to remove that also.

You can use the 200GB as a data partition and/or use 25GB for a test install of another Ubuntu.

Thanks O'fred, As the boot repair log said start  up tried SDA -1, -2 and ended up booting from SDA-5, and 3 is my Ubuntu partition with SDAs  5 & 7 extensions of 3,  I suspect I've a copy of GRUB therein. 

When I boot the first screen is the Ubuntu red or violet screen with Ubuntu the first, and automatic, boot choice on the first line so I'm pretty sure I've grub in my MBR.

I haven't modified fstab to auto mount NTFS  but I'm not absolutely sure one of the startup programs I've used over the years hasn't automatically done so. As I noted, it first tries to boot from sda-1 which is NTFS.

I'll try to puzzle it out  but if I can't find my way on my own I'll check back here, hopefully before bricking my computer. 

Thanks!


: 3      210GB   1000GB  791GB   extended
 7      210GB   512GB   302GB   logical   ext4
 5      512GB   996GB   484GB   logical   ext4
 6      996GB   1000GB  4159MB  logical   linux-swap(v1)

---

### Post by yancek on 2018-04-28
Setting the default menuentry to boot is explained at the link below under the heading setting a main menu entry as the default, count is from zero not one. 

[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

---

### Post by jiminalaska2 on 2018-05-02
Solved.
Windows is gone. New boot partition's set up. No problems noted on startup.
Thanks for the help!

---

