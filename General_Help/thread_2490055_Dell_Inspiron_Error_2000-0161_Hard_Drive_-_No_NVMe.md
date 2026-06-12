---
title: "Dell Inspiron Error 2000-0161 Hard Drive - No NVMe Drive detected on the PCI tag [x]."
date: 2023-08-20
forum: General Help
---

### Post by c-aderhold on 2023-08-20
I'm having trouble booting into my Western Digital HDD on my Dell Inspiron 3583 after what appears to be a successful Ubuntu install.

The install was of Ubuntu 23.04 on a flash drive made following the "Install Ubuntu Desktop" tutorial (Download image, use balenaEtcher, boot from flash drive, etc.).

The specific error I'm getting is from the Dell SupportAssist Pre-boot System Performance Check, error code 2000-0161 Hard Drive - No NVMe Drive detected on the PCI tag*[x]*

This error began after I attempted to overwrite my previously existing install of Ubuntu 22.04.3 LTS with Kali 2023.2.

During the attempted install of Kali, I received an error stating "*Some of your hardware needs non-free firmware files to operate. The firmware can be loaded from removable media ..."*

Based on advice I read online, I skipped through that part and continued with the attempted install.

After getting this error on the first reboot, I tried updating the BIOS per Dell's instructions. I also Googled the issue multiple ways and none of what I found really seemed to be related to a Linux install. I researched NVMe and understood very little except it has something to do with booting. I looked at my computer's BIOS, confirmed Secure boot is off and UEFI/Legacy boot is enabled. I theorized that maybe trying a fresh install of Ubuntu might solve a boot issue, so that's the latest thing I've tried.

When I boot into the OS on the USB, I can see the Hard Drive in the Disks application and it passes the SMART self tests.

Dell tells me if the BIOS update didn't work that I need to buy a new hard drive. I just can't understand why I can get a successful install message and passed self tests and still need a new hard drive.

How can I better understand my issue? Is there anything else I can try to get this thing to boot?

---

### Post by oldfred on 2023-08-20
You posted in the Official flavors sub-forum, but are installing Kali?
Kali is a pen tester, where pen is another name for flash drive. 

At Ubuntu Forums, we do not support pentesting/hacking/cracking software. While Kali Linux is based on debian, a close relative to Ubuntu, it has been primarily developed and geared towards pentesting and as a result, we do not allow threads on Kali Linux here. For support on Kali Linux, please visit the Kali Linux Forums [https://forums.kali.org/](https://forums.kali.org/), Kali replaced Backtrack which is now obsolete.
Not recommended for a new user

My Dell laptop 5310 with 11th Gen Intel and one NVMe drive, just worked with Kubuntu 22.04. 
We regularly post about turning off Secure Boot and changing from RAID to AHCI. I forgot & it just installed. It used Secure Boot and a driver that I previously had not heard of: Intel® VMD. I has been available in the kernel since kernel version  v4.14, but not sure if Ubuntu had it.
I did have to turn off Windows fast startup/hibernation & bitlocker.

---

### Post by c-aderhold on 2023-08-21
>> [COLOR=#000000]You posted in the Official flavors sub-forum, but are installing Kali?

[/COLOR]Hi oldfred, I appreciate your response! I am NOT attempting to installing Kali. I am attempting to reinstall Ubuntu 23.04. My apologies if I was unclear.


I currently have Ubuntu installed on the drive that is failing to boot (please review my original post for details), giving me the Dell Error Code 2000-0161 - Hard Drive - No NVMe Drive detected on the PCI tag [x].

Secure boot is disabled on my machine, and ACHI is enabled.

Is there anything else I can do to troubleshoot?

---

### Post by tea for one on 2023-08-21
Can you boot into an Ubuntu live (Try Ubuntu) session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

---

### Post by oldfred on 2023-08-21
Run the Boot-Repair Report as suggested by tea for one.

Have you updated UEFI to latest available from Dell & updated NVMe firmware. 
Not sure if Dell updates NMVe or you have to go to vendor for updates.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
Dell laptop says must be on A/C power, not battery
sudo fwupdmgr get-devices
man fwupdmgr


We including me many times have suggested changing RAID to AHCI.
Last year I got a new Dell 5310 with Intel 11th gen chip & NVMe drive. I forgot to turn off Secure Boot and change to AHCI before installing. 
It installed without issue and used a different driver for the NVMe drive. It used Intel® VMD driver for the NVMe drive. That is my only dual boot with Windows system.

---

### Post by c-aderhold on 2023-08-21
Okay - I've downloaded and run the boot-repair utility. Please see below for the pastepin:

[https://paste.ubuntu.com/p/MjxdDcSxKK/](https://paste.ubuntu.com/p/MjxdDcSxKK/)

---

### Post by oldfred on 2023-08-21
You have a BIOS boot mode install on sda.
System is UEFI and newer.
BIOS may not support all the latest drivers.
Windows has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012, so most systems now are UEFI.

Drive is gpt partitioned, so install in UEFI boot mode. You do not need bios_grub partition in UEFI mode, but installer will create an ESP - efi system partition.
How you boot install media, UEFI or BIOS is how it then installs. But then system needs to be set to boot in UEFI boot mode as default, or you have to manually select in UEFI boot menu the UEFI entry. It may work now, if you manually select the BIOS/CSM/Legacy boot entry or a BIOS drive entry. Similar to selecting Live installer in F12. But best not to keep BIOS mode boot.

If reinstalling to sda, better to not have just / (root) on a 1TB drive. While that is often easier for new users, that large of a root is not optimal. Suggest 40 or 50GB for / and rest as /home or data partition. If using /home, you need to use Something Else and create / and /home. It will normally create an ESP and create a swap file. If you create partitions in advance with gparted be sure to have ESP as FAT32 with boot,esp flags. 
If your have NVMe drive, and it is seen, it will probably want ESP on that drive.

---

### Post by tea for one on 2023-08-21
oldfred has recommended a highly suitable course of action.

Boot your USB installation medium in UEFI mode
Check via terminal with this command:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Separation of System / from /home is also good practice

---

### Post by c-aderhold on 2023-08-21
> **oldfred said:**
> 

Drive is gpt partitioned, so install in UEFI boot mode. You do not need bios_grub partition in UEFI mode, but installer will create an ESP - efi system partition.
How you boot install media, UEFI or BIOS is how it then installs. But then system needs to be set to boot in UEFI boot mode as default, or you have to manually select in UEFI boot menu the UEFI entry. It may work now, if you manually select the BIOS/CSM/Legacy boot entry or a BIOS drive entry. Similar to selecting Live installer in F12. But best not to keep BIOS mode boot.



The text I see on the screen when hitting f12 at startup is below. I've tried selecting the Onboard NIC option and get the same NVMe error. I used the BIOS Flash Update option when troubleshooting using Dell's resources. Does it mean something new if I'm not seeing my HDD on this menu?

Boot mode is set to:  UEFI; Secure Boot:  OFF; PTT is OFF;

LEGACY EXTERNAL DEVICE BOOT:
     Onboard NIC
OTHER OPTIONS:
     BIOS Setup
     BIOS Flash Update
     Diagnostics
     SupportAssist OS Recovery
     Change Boot Mode Settings
     Exit Boot Menu and Continue

> **oldfred said:**
> 
If reinstalling to sda, better to not have just / (root) on a 1TB drive. While that is often easier for new users, that large of a root is not optimal. Suggest 40 or 50GB for / and rest as /home or data partition. If using /home, you need to use Something Else and create / and /home. It will normally create an ESP and create a swap file. If you create partitions in advance with gparted be sure to have ESP as FAT32 with boot,esp flags. 
If your have NVMe drive, and it is seen, it will probably want ESP on that drive.

Does "reinstalling to sda" mean to try and reinstall the os on my hard drive? I just want to make sure before moving forward and reporting back.

I don't understand your suggestions regarding 40 or 50GB for / and rest as /home or data partition. Is that an important piece of solving my problem? If so, can you point me towards more resources? I tried Googling the above sentence and cannot make sense of the resources that are popping up.

---

### Post by c-aderhold on 2023-08-21
> **tea for one said:**
> oldfred has recommended a highly suitable course of action.

Boot your USB installation medium in UEFI mode
Check via terminal with this command:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Separation of System / from /home is also good practice

This returns the word Legacy. What does that mean?

---

### Post by tea for one on 2023-08-21
> **c-aderhold said:**
> This returns the word Legacy. What does that mean?
It means that you have booted the installer in Legacy mode.
The first priority is to boot in UEFI mode.

---

### Post by oldfred on 2023-08-21
Best to resolve issue with NVMe drive.
But suggestions on partitions were once that was resolved. 
Is NVMe drive shown in UEFI setting, usually f2 with Dell.

---

### Post by tea for one on 2023-08-21
> **oldfred said:**
> Best to resolve issue with NVMe drive..
[COLOR="#0000FF"]Disk sda: 931.51 GiB[/COLOR] was recognised by boot-repair during the live session.
Is there some specific Dell reason why it is invisible in the UEFI settings yet visible by boot-repair?

---

### Post by yancek on 2023-08-21
Boot repair shows a 1TB SATA drive and your USB but no SSD (nvme drive) . Do you have an SSD?  Might be settings in the BIOS you changed when you first had problems.  I would suggest that you reinstall and take care that you select the USB to boot from UEFI boot option in the BIOS.  How to do that varies with manufacturer so you can either explore your BIOS or do an online search for accessing BIOS options on your specific computer.  As suggested above, use a GPT partition table and you can follow the instructions below for using the manual (Something Else) option to install Ubuntu and create a separate /home partition.  You do NOT need all the partitions they suggest, only create and EFI (2-500MB), / (filesystem)(30-50GB) and /home partitions using the rest of the disk.  You could leave some free space for future partitions if you want.

[https://www.linuxteck.com/how-to-install-ubuntu-22-04-lts-step-by-step/](https://www.linuxteck.com/how-to-install-ubuntu-22-04-lts-step-by-step/)

The link below explains it a little better.  Maybe read through both to get a better idea before beginning.  The link below also suggests a /boot and /swap partition which are not necessary.  Ubuntu creates a swap file by default but if you want, you can create a swap partition without problems.  I would just do an EFI, / and /home partition.

[https://ostechnix.com/install-ubuntu-desktop/](https://ostechnix.com/install-ubuntu-desktop/)

---

### Post by tea for one on 2023-08-21
> **yancek said:**
> Boot repair shows a 1TB SATA drive and your USB but no SSD (nvme drive) . [COLOR="#0000FF"]Do you have an SSD?[/COLOR]  
Yes, good question.
The original post mentions:-
> I'm having trouble booting into my Western Digital HDD on my Dell Inspiron 3583 after what appears to be a successful Ubuntu install
The install was of Ubuntu 23.04 on a flash drive made following the "Install Ubuntu Desktop" tutorial (Download image, use balenaEtcher, boot from flash drive, etc.).
The specific error I'm getting is from the Dell SupportAssist Pre-boot System Performance Check, error code 2000-0161 Hard Drive - No NVMe Drive detected on the PCI tag[x]
NVME drive not detected is ambiguous.
[LIST]
[*]Not detected because it does not exist
[*]Not detected because it exists but has a hardware fault
[/LIST]
A little clarification from the OP would be welcome.

---

### Post by c-aderhold on 2023-08-21
Thank you everyone!

The only hard drive installed on my machine is a WD 1tb HDD (Model WDC WD10SPZX-22Z10T1). There is no SSD - I didn't realize the NVMe error was that specific.

It sounds like my fix should be figuring out how to successfully boot into UEFI mode and try reinstalling Ubuntu that way.

---

### Post by tea for one on 2023-08-22
When you boot a USB device to install an operating system, you can sometimes have two options per device if both Legacy and UEFI are allowed in the firmware settings.
The attachment shows the two options.
You need the option beginning with UEFI: (i.e. UEFI followed by a colon)

---

### Post by c-aderhold on 2023-08-22
Thank you, tea for one!

I didn't even notice I had that UEFI option. I've just booted into the live disk using that option and ran the bash code you gave me and it returned UEFI.

My plan is to try the reinstall later this afternoon and I'll report back.

---

### Post by c-aderhold on 2023-08-22
Thanks Everyone!

Booting from the installation disk and running the installer in UEFI mode seems to have been the fix I needed.

After the install was complete, my computer booted right into the OS.

---

### Post by tea for one on 2023-08-22
Good news - well done.
Don't forget to backup your personal data in the future.
Backups are the key to happy computing :D

---

