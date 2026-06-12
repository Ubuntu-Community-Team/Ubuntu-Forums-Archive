---
title: "A question on dumping a running HD to a new HD"
date: 2018-01-07
forum: General Help
---

### Post by satimis on 2018-01-07
Hi all,

I have a PC with following configuration:-

Host	Ubuntu 16.04 desktop
VMs	Ubuntu 16.04 desktop/server/Debien/Mint/Win10 etc
VirtualBox

Hard Drives Configuration
OS	120G SSD
VMs	1.8TB WD HD
Data storage	1TB WD HD

I'm prepared purchasing a 1TB SSD to replace the existing 120G SSD for running OS and VMs as well.  Is there an easy and safe way to dump the running 120G SSD to the new 1TB SSD instead of reinstalling the OS and VirtualBox?

Please advise.  Thanks

When Ubuntu 18.04 LTS will be officially released?

Regards
satimis

---

### Post by HermanAB on 2018-01-07
In a nut shell:
Boot off install media, then use dd to copy the old disk to the new disk.  After that, if the new disk is bigger, run gparted, to expand the file system on the new disk to utilize the whole disk.  Finally, adjust the UUIDs in /etc/fstab to match the new disk.

Doing the above is not exactly difficult, but it is also not easy, since you can mess everything up, if you get the disk names wrong in the dd command.

---

### Post by satimis on 2018-01-07
> **HermanAB said:**
> In a nut shell:
Boot off install media, then use dd to copy the old disk to the new disk.  After that, if the new disk is bigger, run gparted, to expand the file system on the new disk to utilize the whole disk.  Finally, adjust the UUIDs in /etc/fstab to match the new disk.

Hi,

Thanks for your advice.

In the past after booting up the PC with a Live CD or a Live USB I just ran dd command dumping the complete old HD to the new HD.  I haven't run this command for prolonged time.  I wonder whether there is a new way doing it.

I will partition the new 1TB SSD as LVM.

> 
Doing the above is not exactly difficult, but it is also not easy, since you can mess everything up, if you get the disk names wrong in the dd command.
I'll disconnect other HDs first before partitioning the new SSD Drive as well as running dd command to ensure not running any mistake and wiping out all data on the WD HDs

Besides I'll run```

$ sudo fdisk -l

```
to double check

Thanks

Edit:
===
If the official Ubuntu 18.04 will be released soon I'll wait and make a clean installation.  There is no urgency and it is a spare PC.  IIRC the OS of this PC was upgraded from 12.04/14.04 and then 16.04.  I don't know how many space is still available on the /boot partition.

I'll run;```

$ df -h

```
to check it later.

Regards
satimis

---

### Post by HermanAB on 2018-01-07
It helps if all disks have much different sizes, since it is then easier to ensure that you got things right.

---

### Post by oldfred on 2018-01-07
I find new install easier.
And it then becomes a check that your back up procedures work as you still have the old drive to go back and get anything you missed.

And if you use dd, you cannot keep old drive mounted when you reboot with new drive. 
You have to change all partition UUIDs on one drive or the other, if you want to keep the old drive in use.

Some have gotten into a real mess as one boot finds one drive one time and another boot finds the other drive. Depends totally on BIOS and how quick it finds each drive on which is first.

Also if partitions are the newer gpt over the older MBR(msdos), you can only use dd on entire drive,not partitions. And then you have to use gdisk to move backup partition table to end of new drive if drive is larger. 

Will these drives ever get moved to a newer UEFI system? 
If so you may want to consider using gpt. You can still boot in BIOS mode if you have a bios_grub partition. And if using UEFI need an ESP - efi system partition. Neither are large, so do not use much of drive and make it easier to convert from BIOS to UEFI in future. I started converting all new drives back in 2010 to gpt and started adding the ESP when Windows 8 came out using UEFI, even though it was several more years before I got my first UEFI system.

---

### Post by satimis on 2018-01-07
> **HermanAB said:**
> It helps if all disks have much different sizes, since it is then easier to ensure that you got things right.
Your advice noted and thanks

Regards
satimis

---

### Post by satimis on 2018-01-07
> **oldfred said:**
> I find new install easier.
And it then becomes a check that your back up procedures work as you still have the old drive to go back and get anything you missed.

And if you use dd, you cannot keep old drive mounted when you reboot with new drive. 
You have to change all partition UUIDs on one drive or the other, if you want to keep the old drive in use

-snip -
.
Hi,

Yes, you're right.  Especially the Ubuntu OS has been upgraded several times from 12.04 to 16.04  I'll do a new install when Ubuntu 18.04 is officially released.

A further question do I need to disconnect the 2 WD HDs before installing Ubuntu 18.04 and re-connecting them afterwards?  It is for safety reason avoiding wiping out their data accidentally

On the spare PC I have 2 SSDs:-

1) Intel 120G SSD
VirtualBox is running

2) ADATA 120G SSD
OS - Ubuntu 16.04 desktop
Only for running Blender.

Their booting is controlled by BIOS.  The WD 1TB and WD 1.8TB HDs are shared by them.

I'll try installing Epson scanner on ADATA for scanning negative.  Please see my another thread on;
How to scan negative on Epson scannner
[https://ubuntuforums.org/showthread.php?t=2381962](https://ubuntuforums.org/showthread.php?t=2381962)

If successful I'll post the result on above thread.

Regards
satimis

---

### Post by oldfred on 2018-01-07
I typically do not disconnect drives, but it is a lot safer for newer users to disconnect drives, if physically not do difficult.
If not disconnected only use Something Else install option and be sure to select correct drive. And install grub2's boot loader to that same drive. Sometimes drive order changes in BIOS. 
With my system when I had skipped a SATA port a flash drive as sde, would become sdb and every other drive moved up a letter.

I find partitioning in advance with gparted to make process slightly easier. 
But one time on a drive with multiple partitions, I added a smaller partition for root and larger for data. But then during install missed which was which and installed to wrong partition. But did not have data in data partition (yet), so I was ok. But one more reason for good backups, even those of us who think we know what we are doing may make mistakes.

---

