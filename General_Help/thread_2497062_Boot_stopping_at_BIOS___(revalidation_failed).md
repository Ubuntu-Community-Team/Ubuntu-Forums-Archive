---
title: "Boot stopping at BIOS ?  (revalidation failed)"
date: 2024-04-21
forum: General Help
---

### Post by oygle on 2024-04-21
Booting is stopping at the BIOS prompt. When I was able to go into BIOS, the boot order showed 2 entries for Ubuntu ?

Finally it booted and got a "revalidation failed" message.

```

~/Downloads/var_logs_0422$ grep -i -r "revalidation"

```

> 
dmesg.0:[    6.996340] kernel: ata2.00: revalidation failed (errno=-5)
dmesg.0:[   28.050808] kernel: ata2.00: revalidation failed (errno=-5)
dmesg.0:[   33.423917] kernel: ata2.00: revalidation failed (errno=-5)
syslog:Apr 22 07:15:09 Inspiron-3542 kernel: [    7.311968] ata2.00: revalidation failed (errno=-5)
syslog:Apr 22 07:15:09 Inspiron-3542 kernel: [   12.688005] ata2.00: revalidation failed (errno=-5)
dmesg:[    7.311968] kernel: ata2.00: revalidation failed (errno=-5)
dmesg:[   12.688005] kernel: ata2.00: revalidation failed (errno=-5)
kern.log:Apr 22 07:15:09 Inspiron-3542 kernel: [    7.311968] ata2.00: revalidation failed (errno=-5)
kern.log:Apr 22 07:15:09 Inspiron-3542 kernel: [   12.688005] ata2.00: revalidation failed (errno=-5)
syslog.1:Apr 21 06:12:11 Inspiron-3542 kernel: [    6.996340] ata2.00: revalidation failed (errno=-5)
syslog.1:Apr 21 06:12:11 Inspiron-3542 kernel: [   28.050808] ata2.00: revalidation failed (errno=-5)
syslog.1:Apr 21 06:12:11 Inspiron-3542 kernel: [   33.423917] ata2.00: revalidation failed (errno=-5)
kern.log.1:Apr 21 06:12:11 Inspiron-3542 kernel: [    6.996340] ata2.00: revalidation failed (errno=-5)
kern.log.1:Apr 21 06:12:11 Inspiron-3542 kernel: [   28.050808] ata2.00: revalidation failed (errno=-5)
kern.log.1:Apr 21 06:12:11 Inspiron-3542 kernel: [   33.423917] ata2.00: revalidation failed (errno=-5)


Kubuntu system with ..

> 
Operating System: Kubuntu 22.04
KDE Plasma Version: 5.24.7
KDE Frameworks Version: 5.92.0
Qt Version: 5.15.3
Kernel Version: 5.15.0-105-generic (64-bit)
Graphics Platform: X11
Processors: 4 × Intel® Core™ i7-4510U CPU @ 2.00GHz
Memory: 7.7 GiB of RAM
Graphics Processor: Mesa Intel® HD Graphics 4400

---

### Post by oygle on 2024-04-21
Someone having the same problems, same Kubutu version -  [https://discuss.kde.org/t/ata-revalidation-failures-and-comreset-errno-5-and-32/14319](https://discuss.kde.org/t/ata-revalidation-failures-and-comreset-errno-5-and-32/14319)

---

### Post by oldfred on 2024-04-22
What does smartmontools show.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
 What a Failing HDD looks like
[https://ubuntuforums.org/showthread.php?t=2446974](https://ubuntuforums.org/showthread.php?t=2446974)

Have you run fsck or e2fsck on your ext4 partitions. And repair tools on any other formats on drive?
To see all the ext4 partitions
Partition must be unmounted:
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by oygle on 2024-04-22
> **oldfred said:**
> What does smartmontools show.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
 What a Failing HDD looks like
[https://ubuntuforums.org/showthread.php?t=2446974](https://ubuntuforums.org/showthread.php?t=2446974)

I have been running that periodically. It always reports okay. I haven't run the long test as the HDD is nearly 10 years old, and assuming it is starting to fail, I will avoid that type of 'work'activity'.

```
~$ sudo parted -l
```

> 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  2097kB  1049kB                                        bios_grub
 2      2097kB  540MB   538MB   fat32           EFI System Partition  boot, esp
 3      540MB   21.0GB  20.5GB  ext4
 7      21.0GB  26.1GB  5119MB  linux-swap(v1)                        swap
 4      26.1GB  1000GB  974GB   ext4


> **oldfred said:**
> 
Have you run fsck or e2fsck on your ext4 partitions. And repair tools on any other formats on drive?
To see all the ext4 partitions
Partition must be unmounted:

I will avoid running those tools for now. Would have to create a bootable usb as all partitions are on the one HDD. It's not really worth it to attempt to 'repair' a HDD that is 10 years old and had a lot of work. To a *nix systems credit, if I had have used the same laptop in a Windows file system, it would not have lasted 10 years. The laptop has some annoying display problems also, for years, blank screen, can't fix it, not interested in spending the time, ...old technology.

Have now (since posting ) purchased an external SSD. So plan to put Kubuntu on it, copy all the files , then use it as an external (boot) device on a windows 10 laptop. Hopefully that will work out okay. It's a solution for 2 to 3 months.

Thanks for your help.  :)

---

### Post by oldfred on 2024-04-22
I really like my external SSD. My first one was the M.2 SSD from 2017 desktop build when I wanted a newer larger drive. I liked it so much I bought a another M.2 drive and USB adapater, so have two external SSD.
I have UEFI Kubuntu installed on both. First one was install from desktop, but second was a new install & copy of data from desktop. So 3 almost similar systems.

I found I could boot external SSD with Kubuntu in UEFI mode from new Dell laptop with Intel 11th Gen chip and could boot it from very old 2006 BIOS laptop by adding a BIOS version of grub to HDD on old laptop to boot an external drive directly.

---

### Post by oygle on 2024-04-22
> **oldfred said:**
> I really like my external SSD. My first one was the M.2 SSD from 2017 desktop build when I wanted a newer larger drive. I liked it so much I bought a another M.2 drive and USB adapater, so have two external SSD.
I have UEFI Kubuntu installed on both. First one was install from desktop, but second was a new install & copy of data from desktop. So 3 almost similar systems.

I found I could boot external SSD with Kubuntu in UEFI mode from new Dell laptop with Intel 11th Gen chip and could boot it from very old 2006 BIOS laptop by adding a BIOS version of grub to HDD on old laptop to boot an external drive directly.

Thank you, I wish there was a "thumbs up" to give your reply. So, now after reading your post, I feel it is fine to now format the SSD , use **mkusb** to do a Kubuntu boot, and then install Kubuntu on the SSD. Does it matter if I do the install (from the usb stick) to the SSD on the Lenovo/Win10 laptop , or the Dell/Kubuntu laptop ?  I guess it matters none, as it is using the OS on the usb stick.

The partitions on the current Kubuntu (22.04) are shown at [https://ubuntuforums.org/attachment.php?attachmentid=293674&d=1713822059](https://ubuntuforums.org/attachment.php?attachmentid=293674&d=1713822059) .  Is there any advantage in either having additional partitions, or making 'root' and/or 'swap' larger ?  The data is only 105 Gb, as I backup it up to a usb stick, plus an external drive (non SSD).

I see there is a 24.04 LTS Kubuntu, but I don't know how stable it is.

---

### Post by oygle on 2024-04-23
I noticed with the external SSD it was auto mounted when I attached it. When I get it all setup, I will have it permanently attached to a Thunderbolt port on the Lenovo/Win10 laptop. Boot up into Kubuntu automatically, or via GRUB. Are there any rules to safeguard the SSD damaging files ? For example, ensure the laptop power is always on, as a low battery situation may cause problems. I assume one can't do a "Safely Remove" when it is the OS and data and is mounted.

When I want to reboot into Windows10, I guess a shutdown, disconnect the usb cable to the SSD, then power up and into windows, as Windows may get fussy about an EXT file system attached.

---

### Post by oldfred on 2024-04-23
If using 22.04 Kubuntu note that this bug still applies as it uses the Ubiquity installer which defaults to first drive.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Be sure to partition in advance & use gpt partitioning.
Create ESP as first partition, if larger SSD make ESP bit larger. 
You may want to wait a few days and install 24.04, which now uses the Calmares installer and works to install to the ESP on a second drive.

If not an HP, grub install uses efibootmgr to set Ubuntu as first in boot order. It will then be default.
My Dell rebooted to Ubuntu as long as I left it connected. When I removed the external drive it would go to UEFI/BIOS as entry in UEFI for Ubuntu would not work. I had to change default to Windows to boot it first. My Dell calls it "BIOS" but once in BIOS it says it only boots in UEFI mode.
Having ESP on external drive is essential for removable drives.

Installer will create an "ubuntu" entry in UEFI, but if a drive is disconnected that entry is modified or removed & will  not work. You then boot it just like you boot live installer choosing the drive name or label in UEFI boot menu. If using with a different system you have to manually boot from UEFI menu.

---

### Post by oygle on 2024-04-23
> **oldfred said:**
> If using 22.04 Kubuntu note that this bug still applies as it uses the Ubiquity installer which defaults to first drive.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Be sure to partition in advance & use gpt partitioning.
Create ESP as first partition, if larger SSD make ESP bit larger. 
You may want to wait a few days and install 24.04, which now uses the Calmares installer and works to install to the ESP on a second drive.

Thanks for informing me of the bug issue. Does 23.10 fix the bug I wonder ?  Yes, I will use GPT for sure and create the ESP as the first partition. Re waiting a few days, as "sudodus" pointed out at [https://ubuntuforums.org/showthread.php?t=2497062&goto=newpost](https://ubuntuforums.org/showthread.php?t=2497062&goto=newpost) , it would seem 24.04 may be a bit buggy for a while, which I have noted is usually the case. I can do 23.10 and then wait a few months and then 24.04. I usually do a complete reload, not an upgrade when switching versions.

> **oldfred said:**
> Having ESP on external drive is essential for removable drives.

Okay, thanks.

---

### Post by oygle on 2024-05-15
This has worked out to be a great solution, thanks @oldfred. I haven't as yet booted into Windows 10 from GRUB. Is there ANY chance Windows will try and clobber/wipe Kubuntu  ?? I guess do a backup and see what happens, eh.  :)

---

### Post by oldfred on 2024-05-15
My Dell Laptop had major issues & I had to return it for new motherboard. (Twice)
First time both Windows & Ubuntu kept working.
But second time I think Dell forgot to put the old Product key back into the UEFI. So Windows would not boot.
And I could not restore system, install Windows or do just about anything. Kubuntu worked without issue.
Finally the only thing that did work was to use Dell's total restore. That converted it back to as purchased. And totally erased my working Kubuntu on internal drive.

So have used external SSD which for my use is just as fast as when installed. Not sure if I will reinstall Kubuntu to internal drive since SSD works so well. Only issue is sometimes I have to use Dell's F12 to choose boot, internal Windows or external drive. It seems to remember external drive boot where most systems do not remember that. 
I am not a fan of laptops, only have it for when I travel, as main working install is a Desktop install of Kubuntu that I replicate to external SSDs.

---

### Post by oygle on 2024-05-16
> **oldfred said:**
> Finally the only thing that did work was to use Dell's total restore. That converted it back to as purchased. And totally erased my working Kubuntu on internal drive.
.

Thank you for sharing your experiences, @oldfred . I will take the safe route and disconnect the SSD when I need Windows.   :)

---

