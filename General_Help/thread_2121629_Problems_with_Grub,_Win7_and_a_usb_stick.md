---
title: "Problems with Grub, Win7 and a usb stick"
date: 2013-03-02
forum: General Help
---

### Post by RickKnight on 2013-03-02
(posted last night, but can't find in forum so reposting)

Just installed Windows 7 on my system, used boot-repair to fix grub, and now I can't boot without a usb memory stick plugged in. I have 3 drives, 2 500GB and 1 80 GB. The first drive was a 500GB and has Kubuntu 12.04 LTS installed and working with /boot at /dev/sda1 and / at /dev/sda5. The second drive is an 80GB drive with a single partition for my VMs. The third drive is the other 500GB drive with Windows XP installed at /dev/sdc1. Windows hasn't worked for some time so I decided to install Windows 7 over the Windows XP. To do this I had to switch the third drive to be the first drive. I also moved the first drive with linux on it to the second spot and moved the drive with the VMs to third. I ran boot-repair (and update-grub) to change the boot system for the new arrangement. Boot-repair finished with no errors, but when I try to boot, grub complains that it can't find device "e44d14b6-97eb-40d7-8f35-6bc4013024e0" (/dev/sdb1 /boot) and then I get grub rescue. If I plug in a USB memory stick (any USB memory stick!) the system boots fine. I realized I ran boot-repair with the memory stick mounted, so I've re-run boot-repair with a memory stick but I still can't boot without a USB device plugged in. I've also followed the instructions here [http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7](http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7) and I've run grub-install /dev/sda and update-grub from the running system. Nothing seems to help. I have to have a USB stick installed to boot. Can someone please tell me how to fix this?

Thanks,
Rick

---

### Post by schragge on 2013-03-02
Looks like your system enumerates drives in different order depending on whether an USB stick was inserted during boot or not.  When at grub rescue prompt, run ```
ls
``` to see what devices grub sees. Then reboot into your hard disk Kubuntu installation with USB stick plugged in, and look at the output of
```
sudo fdisk -l
``` or ```
parted -l
```

---

### Post by RickKnight on 2013-03-02
> **schragge said:**
> Looks like your system enumerates drives in different order depending on whether an USB stick was inserted during boot or not.  When at grub rescue prompt, run ```
ls
``` to see what devices grub sees. Then reboot into your hard disk Kubuntu installation with USB stick plugged in, and look at the output of
```
sudo fdisk -l
``` or ```
parted -l
```

Thanks for the reply.

Ok, I booted without the USB stick and got the Grub rescue window, I entered ls, I got ...
```
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1) (fd0)
```
Then I booted with the USB stick and opened the Grub console and entered ls, I got ...
```
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos1) (hd2) (hd2,msdos6) (hd2,msdos5) (hd2,msdos1) (hd3) (hd3,msdos5) (fd0)
```

After booting I ran parted -l ...
```
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  52.4GB  52.4GB  primary   ntfs            boot
 2      52.4GB  500GB   448GB   extended
 5      52.4GB  393GB   341GB   logical   ext3
 6      393GB   498GB   105GB   logical
 7      498GB   500GB   2007MB  logical   linux-swap(v1)


Model: ATA ST3500630AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  197MB  197MB   primary   ext3
 2      197MB   500GB  500GB   extended
 5      197MB   498GB  498GB   logical   ext3            boot
 6      498GB   500GB  2007MB  logical   linux-swap(v1)


Model: ATA ST3808110AS (scsi)
Disk /dev/sdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  80.0GB  80.0GB  extended
 5      64.5kB  80.0GB  80.0GB  logical   ext3


Model: Lexar JD Secure II + (scsi)
Disk /dev/sdd: 2005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  2004MB  2004MB  primary  fat32        boot, lba

```
It looks like you're correct, my system is enumerating the drives differently depending on whether the USB stick is plugged in or not. So, now the question is, how do I fix this, or can I?

Thanks again,
Rick

---

### Post by oldfred on 2013-03-02
It really should not matter. You keep Windows as sda and its boot loader in sda. And install grub in the other drives and set BIOS to boot whichever you prefer. 
Boot-Repair should let you reinstall grub to MBR of hard drives. Of if you can boot from any drive you can just install grub to the MBR of that drive. But grub also remembers where to reinstall so you may need to update that. Major updates of grub will do an auto reinstall to the default location.
With multiple drives you should only do Something else or manual install, so you get the choice on where to install the grub2 boot loader. Otherwise it defaults to sda and some systems may change flash drive to sda. It may depend on what port on motherboard you have in the first drive. I skipped port 2 on my system and sometimes flash drive is sdc and others sde.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by RickKnight on 2013-03-02
> **oldfred said:**
> It really should not matter. You keep Windows as sda and its boot loader in sda. And install grub in the other drives and set BIOS to boot whichever you prefer. 
Boot-Repair should let you reinstall grub to MBR of hard drives. Of if you can boot from any drive you can just install grub to the MBR of that drive. But grub also remembers where to reinstall so you may need to update that. Major updates of grub will do an auto reinstall to the default location.
With multiple drives you should only do Something else or manual install, so you get the choice on where to install the grub2 boot loader. Otherwise it defaults to sda and some systems may change flash drive to sda. It may depend on what port on motherboard you have in the first drive. I skipped port 2 on my system and sometimes flash drive is sdc and others sde.
<< snipped >>

It does matter to some extent as my (Dell) bios boots from the first drive and I don't see any way to change that. I have been able to boot Windows on the first drive after restoring the MBR. I can restore grub to the first drive's boot sector and install grub to /boot on the second drive, but if the bios doesn't see the second drive, grub won't boot any drive. I would have to install grub to the first drive and I don't have any room available for that. But, I have found a solution. My bios gives me 3 choices for USB operation, On, Off and No Boot. In the No Boot mode I can use my USB devices but bios cannot boot from them. also all of my drives are available whether I have a USB stick mounted or not. Since I never boot a USB drive on this system, problem solved.

Thanks,
Rick

---

