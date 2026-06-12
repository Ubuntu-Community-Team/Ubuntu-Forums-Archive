---
title: "Dual Boot Linux and Windows"
date: 2014-06-10
forum: General Help
---

### Post by Bubblegut on 2014-06-10
I want to play DayZ but it is a Windows based game. I am aware of the Wine/PlayOnLinux version but I would rather just play the game normally (there are other games for Windows I want as well). So, how would you dual-boot Windows and Linux when Linux is the main OS? I know it's far easier to add Linux to a Windows system, but this is the situation I am in.

---

### Post by Bubblegut on 2014-06-10
I want to play DayZ but it is a Windows based game. I am aware of the Wine/PlayOnLinux version but I would rather just play the game normally (there are other games for Windows I want as well). So, how would you dual-boot Windows and Linux when Linux is the main OS? I know it's far easier to add Linux to a Windows system, but this is the situation I am in.

---

### Post by oldfred on 2014-06-10
What partitions have you already used. And is system new UEFI or older BIOS based? And what version of Windows? 7 or 8?
Is system laptop or desktop? If desktop easier to add another drive and make it Windows only.

If BIOS, you need a primary partition (sda1 thru sda4) formatted NTFS with the boot flag to be able to install Windows.
UEFI has requirements for more partitions but with gpt partitioning that is not an issue. You just need unallocated space.

Post this:
sudo parted -l

Merged threads, please do not create duplicate threads on same topic. We all are volunteers and need to know what else has been suggested to avoid wasting our time repeating it.

---

### Post by Bubblegut on 2014-06-12
Model: ATA Hitachi HDS72107 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  744GB  744GB   primary   ext4            boot
 2      744GB   750GB  6181MB  extended
 5      744GB   750GB  6181MB  logical   linux-swap(v1)




Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End     Size    Type     File system  Flags
 1      4096B  4010MB  4010MB  primary  fat32        boot, lba

---

### Post by oldfred on 2014-06-13
You have two primary partitions available with your MBR(msdos) partitioning.

So shrink your sda1 using gparted, create a new primary NTFS partition and move boot flag to it. Grub does not use boot flag, but Windows has to have a boot flag on a primary partition to know what partition to boot from, install into, or repair.

You will need your Ubuntu live installer to restore grub2's boot loader and then run sudo update-grub to add the new Windows boot entry to the menu.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Shows both Ubuntu second and Windows second.
 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

 
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
BIOS/Grub/Ubuntu  boot process
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)

---

