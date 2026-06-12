---
title: "Installation on new hardware"
date: 2021-03-10
forum: General Help
---

### Post by SteelCore on 2021-03-10
I have a new Dell PC with a 1 TB normal hard disk and a 500 GB M2 SSD. I've always installed Ubuntu on a single normal SATA hard drive but this new configuration is not as straightforward. I'd like to use the SSD for speed but I also don't want to waste the HHD. Is there a recommended way to do this installation. Thanks for any help.

---

### Post by CelticWarrior on 2021-03-10
Install in the SSD. Use the HDD for data.

---

### Post by SteelCore on 2021-03-10
I do realize that. It's the how that I'm not sure about.

---

### Post by CelticWarrior on 2021-03-10
Is it dual-boot or only Ubuntu?
If only Ubuntu just select the SSD during installation and then later format the HDD from the installed Ubuntu.
UEFI settings may need change: Use AHCI for drives' mode, not Intel RST or RAID (this may not be applicable to your case). Use UEFI only, not Legacy/CSM or UEFI+Legacy. Disable Secure Boot (optional) and Fast Boot (for convenience and better results). Yes, as always, you need to familiarize yourself with your specific UEFI ("BIOS") settings.

---

### Post by mIk3_08 on 2021-03-10
> **SteelCore said:**
> I do realize that. It's the how that I'm not sure about.
Yes. That is a great idea. I've also uses that for many years now. HDD as my back-up data storage and it is more safe using it with the enclosure. It is more safe to have a backup of your important data set aside. I prefer to have a back up disk out here its because internet here in the Philippines is so expensive and unreliable, unstable with data capping of course. Its a business strategy though. You know already business. Its part of the game strategy.

---

### Post by SteelCore on 2021-03-10
> **CelticWarrior said:**
> Is it dual-boot or only Ubuntu?
If only Ubuntu just select the SSD during installation and then later format the HDD from the installed Ubuntu.
UEFI settings may need change: Use AHCI for drives' mode, not Intel RST or RAID (this may not be applicable to your case). Use UEFI only, not Legacy/CSM or UEFI+Legacy. Disable Secure Boot (optional) and Fast Boot (for convenience and better results). Yes, as always, you need to familiarize yourself with your specific UEFI ("BIOS") settings.

Thank you for the reply. The device isn't dual boot, only Ubuntu. It was only a simple BIOS when I last installed 16.04 which I'm still using today. I'll have to dissect and digest these UEFI details you pointed out.

---

### Post by oldfred on 2021-03-10
If UEFI better to use gpt partitioning. But with Ubuntu you can use MBR, but really should not.
If only Ubuntu you also can use gpt with BIOS boot.

If pre-installed with Ubuntu then you may not need all these typical Dell settings:
Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.

My desktop from 2006 was 250GB m.2 SSD & 1TB HDD. I had several copies of Ubuntu on SSD and all data on HDD mounted as /mnt/data partition and all folders normally in /home in the data partition. Also some hidden folders in /home like Firefox & Thunderbird profiles also moved to data partition. I do not fully allocate entire drive, especially the SSD.  But my data is not huge and with new 500GB m.2 NVMe drive, I moved my /mnt/data to SSD and HDD is mostly backup and test installs. 

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

