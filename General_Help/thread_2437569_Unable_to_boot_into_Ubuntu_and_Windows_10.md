---
title: "Unable to boot into Ubuntu and Windows 10"
date: 2020-02-25
forum: General Help
---

### Post by mohyddin on 2020-02-25
Hi, this is my first question here, so please bear with me if I couldn't explain my situation properly.
I have two disks on my laptop and it had windows 10 initially on the first disk /dev/sda. So I decided to install Ubuntu 19 on the second one /dev/sdb and have dual boot. I created a ext4 partition for os and an 8 gb swap and a 512mb efi partition and selected installed Ubuntu boot loader on /dev/sdb, but after it finished Grub didn't work and I can't even boot into windows anymore, I played with the enable/disable legacy mode in bios with no success either. It always says no bootable device found. however, if I select choose device to boot from using F9 on my laptop, I have an option called boot from uefi file and from there I have Ubuntu and Boot if I traverse into /ubuntu/grub64.efi and I can log into my ubuntu os but nothing else works for windows. I tried to use boot-repair from live Ubuntu stick but it fails saying you need to use boot-repair in live media device which I am! I exported the boot-repai info to [https://paste.ubuntu.com/p/9q6k7m35gn](https://paste.ubuntu.com/p/9q6k7m35gn)
any help guys? I would really appreciate it.

---

### Post by yancek on 2020-02-26
Your windows install shows as being on sdb in boot repair, that is the 223GB drive and the first patition has a windows (ntfs) filesystem and the 2nd partition has an EFI partition.  The EFI partition as you can see has only Ubuntu files on it.
The sda drive shows 2 windows partitions, one with the OS system and one a recovery partition on the 119GB drive.  Boot repair shows that sdb has windows code in the MBR which would indicate it is a Legacy rather than an EFI install.  Is this an upgrade from windows 7?  Was windows installed EFI previously?  I ask because boot repair shows nothing to indicate it was.

Beginning at line 584 of boot repair, it indicates you left windows hibernated hence the message and might be why complete info is not available.  The problem with that is you can not turn that off from Linux.  Both your drives appear to be msdos drives and not gpt so windows would not use EFI on those drives.  The grub.cfg file entries also show msdos so windows won't install EFI.  You need to clarify which physical drive had the windows OS on it as you have ntfs partitions on both drives.  You appear to have mixed UEFI with Legacy/CSM installs.  THe ubuntu documentation page at the link below explains the problems that will cause.  You might be able to resolve this by converting to Legacy.  

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-02-26
Windows only installs in BIOS boot mode to MBR(msdos) partitioned drives.
Windows only installs in UEFI boot mode to gpt(GUID) partitioned drives.
Ubuntu will let you install in UEFI mode to MBR, but probably should not.

Windows also installs boot loader & boot partition to drive set as default boot when installed. 
It looks like you had sdb as default boot & main install to sda.
You cannot have a BIOS boot on same drive as UEFI boot.
Windows has to have boot flag on its boot partition, your sdb1 and UEFI requires boot flag on the ESP, your sdb2.
And you only can have one boot flag per drive.

Move boot flag on sdb back to sdb1 and I expect Windows to boot, if system set for BIOS/Legacy/CSM boot.
But you have newer UEFI based system and should consider an UEFI install of Windows.
Microsoft has required vendors to install Windows in UEFI/gpt since Windows 8 released in 2012.

You can use Boot-Repair to convert Ubuntu install on sdb to BIOS boot. But best with two drives to have Windows boot loader on Windows drive and Ubuntu/grub boot loader on Ubuntu drive. You actually have both booting from sdb, but can install grub to MBR or sda (the Windows drive) to boot Ubuntu on sdb. And Windows BIOS boot load on sdb will boot thru boot partition on sdb to loader Windows on sda. Bit confusing.

Do not use Boot-Repair auto-fix as it will install grub to both drives. 
You really want a Windows boot loader on one drive in BIOS mode as grub only boots working Windows and must sometimes directly boot Windows using its boot loader. With UEFI you can always boot either system from UEFI boot menu.

---

### Post by mohyddin on 2020-02-26
sorry if i missed providing information, but I am really finding it frustrating. and I'm using my phone to use this forum as I'm trying to fix this laptop for days no sleep now. I still can't fully follow along your explanations, sounds very technical but hope this would allow you to help me. so initially I had windows 10 installed and it came with the laptop which is new last year i got it so probably not a windows 7 upgrade, I have an internal m2 disk where windows is installed and another ssd which was used for data and that is sdb1 to clarify you guess, so i wanted to install ubuntu on the ssd, but before that I decided to backup my windows so I took an image using clonezilla but before creating an image it complained about having MBR and GPT partitions so it suggested using sgdisk to remove GPT as I read most suggestions were on the internet, maybe I messed up here, but it said that image was created successfully so i moved to install the ubuntu, launched bootable ubuntu created the swap, root and efi partition,etc.. and when done nothing was bootable, even if I change BIOS setting to UEFI only or legacy, however if I press F9 and select boot from uefi file i can find the shim64 and boot Ubuntu but windows there seems to be no bootloader maybe i deleted it someway but sure how, I have important data and programs on windows partition so i would rather delete ubuntu and reinstall if that gets window to boot, the sda disk contain only the windows C: partition and another one for recovery came with the latop which is hp x360 br-1xx btw. I still find GPT, MBR, UEFi, Legacy all these terms very frustrating and hard to get around. I would really be grateful if you could help me out, and If you need any additional info that I may have missed please tell what is it and I will get it to you. Thanks so much!

---

### Post by oldfred on 2020-02-26
Re-read details above.
First move boot flag from sdb2 to sdb1.

You should be able to use Ubuntu live installer, so you do not have to use phone.

More explanation of terms with links to even more detail at bottom of link below in my signature.
See section on Acronyms.

---

### Post by mohyddin on 2020-02-26
Thanks, actually I deleted the boot partition of ubuntu which was on sdb2 and I only have boot flag on the windows at sda1 but still can't boot into windows. not sure what to do as when I took an image of the the windows hdd it said there was a mismatch and found MBR and GPT in sda so it suggested running sgdisk -z /dev/sda before taking the image which I have done so maybe that has to do with it? maybe it was already uefi windows in the first place? cause the output I shared was done after that

---

### Post by oldfred on 2020-02-26
When you have a new system it is normally gpt partitioned with UEFI boot.
But if you reinstall Windows in BIOS mode, Windows incorrectly converts drive from gpt to MBR and leaves the backup gpt partition table.

Not sure what you did originally. 

Your sda1 does not have all the boot files. It needs bootmgr & /boot/BCD. If you have boot flag on sda1, you should be able to run Windows repairs on that partition and restore those files.
Windows has boot partition as a standard, but does not have to have it. 
If you have copies to bootmgr & /boot/BCD, you could try putting them into sda1. But I expect you still need repairs as old boot partition was on different drive & BCD would need updates.

---

