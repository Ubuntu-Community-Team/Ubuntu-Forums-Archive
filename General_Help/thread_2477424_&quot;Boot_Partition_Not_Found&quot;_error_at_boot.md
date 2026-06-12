---
title: "&quot;Boot Partition Not Found&quot; error at boot"
date: 2022-07-24
forum: General Help
---

### Post by xeddog on 2022-07-24
I have an Ubuntu 22.04 installation that has been running perfectly for 2 years.  Today when I turned the machine on, I got the subject message.  

I booted a start-up disk, and using gparted I see there are 3 "partitions" on /sda.  1.  513MB Unallocated   2.  /dev/sda2 ext4 (/mnt/boot-sav/sda2  And 3.  15.69GB Unallocated.  Nothing else.   /sda is only used for the OS, my home directory is on /sdb, and all important data is kept on a NAS.

I have researched until my head hurt, but I tried using the boot-repair utility to see about re-installing GRUB.  For that, I get a long message about GPT detected, please create a bios-boot partition (>1MB, unformatted filesystem, bios_grub flag)...  Back to gparted to try and create it.  Some of the tutorials I read said to either create it as GPT,  but my gparted has no option for that.

That brings me here.  Is there a clear tutorial I can follow to recover this disk?  I would really hate to lose it because of the applications on it.  They are a rpita to configure and would probably take me days to do.  All of my important data is kept on my NAS.

Thanks,

Wayne

---

### Post by oldfred on 2022-07-24
You only need a bios_grub partition if booting in old BIOS mode.
How you boot install media, UEFI or BIOS is then how it installs or repairs.
It seems system must be UEFI and did not see an ESP, either missing or corrupted.

You should have good backups. But all your user settings are in /home.
Only if you installed server apps in / or have edited system files do you need those backed up.
But a lot easier to reinstall if you also export list of installed apps to make it easy to reinstall everything. I make that export part of my rsync backup script. 

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

If just file corruption from abnormal shutdown or power failure fsck on ext4 and dosfsck on FAT32 may be required.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

If bigger issue like failing drive, you can check in Disks, the smartstatus. Icon in upper right corner.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks is Smart Data:
[https://askubuntu.com/questions/983619/s-m-a-r-t-data-no-longer-available-in-ubuntu-16-04-disks-application](https://askubuntu.com/questions/983619/s-m-a-r-t-data-no-longer-available-in-ubuntu-16-04-disks-application)
 What a Failing HDD looks like
[https://ubuntuforums.org/showthread.php?t=2446974](https://ubuntuforums.org/showthread.php?t=2446974)
gsmartcontrol
sudo apt install smartmontools

---

### Post by xeddog on 2022-07-28
All hell has broken loose in the household, but I finally got the boot info done.  Here is the link [https://paste.ubuntu.com/p/Y5sdKpX5Nr/](https://paste.ubuntu.com/p/Y5sdKpX5Nr/) .

---

### Post by yancek on 2022-07-28
> I have an Ubuntu 22.04 installation that has been running perfectly for 2 years 

I imagine that is a typo as 22.04 has only been out for 3 months.  Also, boot repair shows you have 20.04 installed.  It also shows you have Syslinux in the MBR of the Ubuntu drive.  Ubuntu uses Grub so that may have happened if you tried to repair using the boot repair tool.  Your first partition on the drive is a swap partition.  Did you do that when installing as a default Ubuntu will not do that but will create a swap file.  Was that perhaps an EFI partition?  You can use the suggestion in boot repair to create a BIOS_Boot partition or you can create an EFI partition.  If you create an EFI partition, you need to boot the Ubuntu installer in UEFI mode.  If you want it in Legacy mode, you should boot in Legacy mode which you did when you ran boot repair.  In either case, you will need to reinstall Grub.

---

### Post by oldfred on 2022-07-28
You have this entry in fstab, which says your installs was UEFI.
> # /boot/efi was on /dev/sda1 during installation
UUID=E9D5-2903  /boot/efi       vfat    defaults        0       1


But that UUID does not exist, and sda1 is now swap?
Did you convert ESP - efi system partition to swap?

---

### Post by xeddog on 2022-07-29
Sorry for the confusion.  I am not usually this disorganized, but did I mention the chaos in the house?  (including one old self-centered ******* with prostate cancer and dementia) Anyway, Yes, THIS machine is 20.04.  I have another machine that is also 20.04, but I am trying to get it upgraded to 22.04 and I had that on my mind (what's left of it) at the time.  And that one partition shown as swap was just me playing with it and forgot to remove it.  It was unallocated space.

Now the good news.  I got it back!  It was almost the definition of insanity, but not quite.  THIS time, after launching boot-repair, when it asked whether or not to update, I let it update.  I did not do the update in earlier attempts because it just seemed like a fresh download should have been up to date.  Lesson learned.  After the update, it said to do this and do that, so I do'd this and I do'd that.  And it's back.

So thank you for the assistance, and sorry for the confusion.


Wayne

---

