---
title: "Boot is too slow (more than 1 hour)"
date: 2017-08-11
forum: General Help
---

### Post by elstongunnn on 2017-08-11
I have windows 10 and yesterday night I installed ubuntu 16.04 LTS, but  today I reboot it and it took more than one hour. This are some of the  messages that appeared.

[http://imgur.com/a/iHyni](http://imgur.com/a/iHyni)

and then appeared some messages like "(something)... Done" in green, and then ubuntu started.
What can I do?

---

### Post by elstongunnn on 2017-08-11
I restarted again and it took half an hour to boot, but the screen was always in plain purple colour. Any help?

---

### Post by oldos2er on 2017-08-11
Please post your full hardware specs.

---

### Post by oldfred on 2017-08-11
And specifically what is ata2, or probably 2nd drive.
Post this:
 sudo lshw -C Disk -short 



Did you leave in a flash drive & does it boot ok if you remove it?
One user had a DVD and for some strange reason the system wanted to run fsck on the DVD.

Or you may need a boot parameter to work around a hardware issue.

---

### Post by elstongunnn on 2017-08-12
> **oldos2er said:**
> Please post your full hardware specs.

My laptop is a Samsung Series 5 Ultra: i5,500gb HDD (80gb for ubuntu, 420gb for windows 10), 4gb RAM...

> **oldfred said:**
> And specifically what is ata2, or probably 2nd drive.
Post this:
sudo lshw -C Disk -short 



Did you leave in a flash drive & does it boot ok if you remove it?
One user had a DVD and for some strange reason the system wanted to run fsck on the DVD.

Or you may need a boot parameter to work around a hardware issue.

I don't know what is ata2. I have a 500gb HDD, where 21 gb are in "disk 1" (I don't know what this is, but I didn't touch that), and the rest are in "disk 0". In "disk 0", I have 400 gb for windows 10 and 80 gb for ubuntu.

I booted from a USB but know I'm booting from my HDD. There's no USB connected, and my laptop don't have any CD or DVD reader.

I wrote sudo lshw -C Disk -short  and it said USB but was replaced by SCSI and then:

*-disk                  
       description: ATA Disk
       product: Hitachi HTS54505
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: A6C0
       serial: TE95113QJH1JXP
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=9045ff79
  *-disk
       description: ATA Disk
       product: SanDisk SSD i100
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 1.04
       serial: 121500139961
       size: 22GiB (24GB)
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512

---

### Post by elstongunnn on 2017-08-12
note: "dos" means "two" (2) in spanish

---

### Post by oldfred on 2017-08-12
You have an UltraBook which vendor did for a while where they added a small 16 to 32GB SSD only for Windows boot cache. Often called Intel SRT as that was the software in UEFI/BIOS.
It is seen as a second drive, but the Intel SRT is seen as RAID and normal desktop installs do not have the RAID driver.

Many with the smaller SSD, have used it just for Ubuntu / (root) with /home on HDD. Then all of Ubuntu is fast, where with Windows it is just used for initial boot.

You may just need RAID driver, but not sure which one, if you do not want to turn off Intel SRT in UEFI and use AHCI only. 

First try just installing the RAID drivers.
 sudo apt-get install mdadm
sudo apt-get install dmraid 

      
  Intel Smart Response Technology
[URL="http://mjg59.dreamwidth.org/26022.html"]http://mjg59.dreamwidth.org/26022.html
[/URL]
 SRT Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382) 

[URL="http://mjg59.dreamwidth.org/26022.html"]
[/URL]

---

### Post by elstongunnn on 2017-08-12
> **oldfred said:**
> 
First try just installing the RAID drivers.
 sudo apt-get install mdadm
sudo apt-get install dmraid 

[URL="http://mjg59.dreamwidth.org/26022.html"]
[/URL]

Nope, this doesn't work. What can I do now? :-(

---

### Post by oldfred on 2017-08-12
Change to AHCI mode in UEFI/BIOS.
You will need to install Windows AHCI driver first.
And then the boot cache will not work, but otherwise Windows still should work.

---

### Post by elstongunnn on 2017-08-12
> **oldfred said:**
> Change to AHCI mode in UEFI/BIOS.
You will need to install Windows AHCI driver first.
And then the boot cache will not work, but otherwise Windows still should work.


Can you please tell me any tutorial or something to do this?

---

### Post by oldfred on 2017-08-12
Other Samsung threads. 
Issues are common by brand, so most of these issue may apply to your system.
Users usually have posted what they did.

 Phoenix SecureCore Tiano bios setup and secure boot is greyed out. You need to set a Supervisor Password in the Security tab
Samsung w/ Phoenix Tiano SecureCore
[http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267](http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267)
Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

