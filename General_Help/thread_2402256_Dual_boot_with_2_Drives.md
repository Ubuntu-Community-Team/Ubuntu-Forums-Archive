---
title: "Dual boot with 2 Drives?"
date: 2018-09-27
forum: General Help
---

### Post by doom1993 on 2018-09-27
I want to Dual-Boot Ubuntu 18.04.1 with Windows 10 64-Bit on a Dell Inspiron 5680 with a 128GB SSD and 1TB HDD. Windows is already installed on the SSD and the HDD is used for storage and pagefiles. How would i go about installing Ubuntu on the HDD while still leaving a NTFS partition on the HDD for Windows? My BIOS is UEFI and Secure Boot is enabled.

---

### Post by oldfred on 2018-09-27
Is HDD partitioned as gpt?
Post this from live installer in live mode:
sudo parted -l

Use Windows tools to shrink NTFS partition on HDD, reboot Windows & run chkdsk on that partition.
Can you then unplug SSD or turn it off in UEFI, so not seen? If not grub will probably install to ESP on SSD. That can work, but I prefer to at lease have an ESP on HDD, even if not immediately used.
And then use Something else to install, so you can choose to use HDD drive.  

Dell needs UEFI update & SSD firmware update.
It needs drive settings in UEFI changed from RAID or Intel SRT to AHCI. Add AHCI driver into Windows first.

 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 

See general instructions in link in my signature below.

With 18.04 you only need an ESP & / (root). Swap is now a file, not a partition. Many like separate /home and/or data partition(s). You already have an NTFS that can be a shared data partition, but Windows fast start up must be off, or it is seen as hibernated. And Windows turns fast startup back on with updates.

      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by doom1993 on 2018-09-28
"[COLOR=#000000]Can you then unplug SSD or turn it off in UEFI, so not seen? If not grub will probably install to ESP on SSD. That can work, but I prefer to at lease have an ESP on HDD, even if not immediately used."

There is no option in UEFI to turn it off and i don't want to unplug it unless i have to, is there a workaround or do i have to unplug it?[/COLOR]

---

### Post by oldfred on 2018-09-28
You do not have to unplug it. but use Something Else install option.

I have multiple Ubuntu installs, and my new install always overwrites the /EFI/ubuntu folder in the ESP on sda. 
In your case it will just add a folder into the ESP, next to the /EFI/Microsoft folder to boot Windows.
But best to also create an ESP, FAT32 with boot flag on HDD. It may not be used as with UEFI install grub only wants to install to first ESP. 

I quickly learned to backup ESP, as most do not, and then restore my default boot. But I copy entire /EFI/ubuntu folder from ESP on sda, to an ESP on sdb. So then I could create a boot on sdb without having sda drive at all.  It really then is just another backup.

If not unplugging SSD, you must use Something Else. 
While you can add / (root) partition as ext4 during install to space you created on sdb, I prefer to partiiton with gparted first. You still have to use Something Else and choose (change button) to use a partition you create in advance.
You only now need ESP & / on sdb. The 18.04 installer creates a swap file, rather than a swap partition, but installer will use a swap partition if you have one.

---

### Post by doom1993 on 2018-09-28
Would it be better and easier if i just unplug the SSD for install?

---

### Post by oldfred on 2018-09-28
Totally up to you.

Often unplugging a drive causes UEFI to lose the entries. Windows is usually automatically found. But best to have a Windows repair flash drive, so if needed you can run Windows repairs.
And of course always have good backups.

---

