---
title: "Ubuntu Studio 22.04 Grub boots into recovery mode after Gmod misahap."
date: 2022-11-12
forum: General Help
---

### Post by jukingeo on 2022-11-12
Hello All,

I am having an issue with Grub during a reinstall of Ubuntu Studio 22.04.

First a bit of history on this issue.

My son was playing a game through Steam (Gmod) and he accidentally pressed the Shift and Windows key.  The screen went black and displayed this error message:
[I]
x86 CPU: SGX disabled by bios.[/I]

While I initially went this route and was looking for issues with SGX, I had eventually found out that the machine (normally) boots through this message and goes into the boot loader (Grub) and boots up.   However, this wasn't happening.  Every time I started Ubuntu I would get that message.  Doing a bit of digging, I had found out that it could be a HDD issue.   After doing some tests I ruled that out and just bit into the sour apple and reinstalled my Ubuntu 22.04.

Upon completion of the installation, I encountered a new issue.   Grub wouldn't start the system up, it would boot into recovery mode and I am presented with a prompt.   I don't know what to do from there.    Now if I boot my computer and bypass the boot drive and go directly to where Ubuntu is loaded in, the OS boots up fine. 

So this tells me that the whole time Grub was corrupted.   Also what it is telling me is that a subsequent re-install of Ubuntu doesn't solve the problem.  Grub stays corrupted.

Now, I have looked on-line and had found that the easiest method to fix the issue was to use a program called "Boot Repair".    The instructions tell you to boot Ubuntu 22.04 from the live USB and then install Boot Repair from the terminal.  Okay so that part is fine, but when the instructions say to click "Recommended Fix" I then get ANOTHER error message saying that the BIOS cannnot be in Legacy mode.

Now to add to insult to injury, when I go back into the BIOS and disable the Legacy mode, I now can no longer access the USB drive which has Ubuntu on it and as the instructions say, you need to boot from the live (USB) mode of Ubuntu 22.04.

Can anyone see the issue with this?  It is a catch 22.  The program doesn't like Legacy mode, but it is needed to even have the USB drive show up.

The only other repair procedure I had found on-line required an enormous amount of hoop jumping and terminal usage.  Much more than I am comfortable with.

I have not found a way to do it through Grub recovery.  Is there a way to fix it that way?

So, what do I do now?   It is a pain to have to sit by my machine as it boots up and go into the boot menu to select the drive where the Ubuntu OS is sitting on to boot it...every time.   And yes, I have looked into the boot menu in the bios and the drive where Ubuntu is sitting on doesn't show up in the boot menu.  Only the USB, DVD drive and the C drive shows up.

Finally, I am flabbergasted that a simple key combination mishap could cause corruption of Grub.  That is something that I would like to have explained to me as I can't see how playing a game could ruin the bootloader.   If you ask me that is ridiculous.

Thank you,
Geo

---

### Post by oldfred on 2022-11-12
As Boot-Repair recommends when asking for help, post the link to the summary report it creates.

Did you originally have an UEFI install & reinstalled in old BIOS boot mode.
So then two different versions of grub and system booting old version?

What setting is UEFI, UEFI only, UEFI & legacy or Legacy/BIOS/CSM boot mode.
Most systems have that setting as default for your install and whether UEFI/BIOS looks to ESP for UEFI boot files or MBR for BIOS boot.

What brand/model system?
 Lenovo has some issues.
[https://support.lenovo.com/us/en/solutions/ps500174-intel-software-guard-extensions-sgx-vulnerabilities](https://support.lenovo.com/us/en/solutions/ps500174-intel-software-guard-extensions-sgx-vulnerabilities)
[https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04](https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04)

---

### Post by jukingeo on 2022-11-12
> **oldfred said:**
> As Boot-Repair recommends when asking for help, post the link to the summary report it creates.

Sorry, don't know how to do that.

> 
Did you originally have an UEFI install & reinstalled in old BIOS boot mode.
So then two different versions of grub and system booting old version?

Well, this happened when my son keyed in some crazy key combo when playing GMod.  He was kicked out of Ubuntu and then the system wouldn't log in.  Like I said in my initial post, the system booted to the point of that "SGX disabled in BIOS" message.  It was later on that I discovered that wasn't an issue and what happened was that the bootloader (Grub) was somehow obliterated.   As for UEFI or Old Boot, how could I tell what was what when it reinstalled?

> What setting is UEFI, UEFI only, UEFI & legacy or Legacy/BIOS/CSM boot mode.
Most systems have that setting as default for your install and whether UEFI/BIOS looks to ESP for UEFI boot files or MBR for BIOS boot.

I think it is both.  I know USB is Legacy because when I turn it off, I cannot boot from the USB drive anymore as I mentioned in the "Catch 22" above.

> What brand/model system?
 Lenovo has some issues.
[https://support.lenovo.com/us/en/solutions/ps500174-intel-software-guard-extensions-sgx-vulnerabilities](https://support.lenovo.com/us/en/solutions/ps500174-intel-software-guard-extensions-sgx-vulnerabilities)
[https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04](https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04)

It isn't a Lenovo, but a computer I built myself based on a GIGABYTE GA-Z270M-D3H LGA1151 mobo with an Intel i7 6700k processor

It has 16 gig Corsair memory.   750 watt Corsair power supply.   About 3 Terrabytes of storage across 3 Samsung SSHD's  

It is running both Windows 7 and, of course, Ubuntu 22.04.

Incidentally, I can get to each operating system through the boot menu, but neither operating system boots automatically.  Windows has its own partition and I am fine with that, but Ubuntu booted in via grub.

In a way I am kicking myself now for reinstalling Ubuntu since it didn't solve the problem and I have to start all over with it.

Now when I boot, Grub goes right into recovery mode.  Is there a way to fix it (without too  much hoop jumping as I don't like that)?

Thanks,
Geo

---

### Post by dragonfly41 on 2022-11-12
Have you searched for threads discussing the original error message ..

*x86 CPU: SGX disabled by bios.*

[https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04](https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04)

---

### Post by oldfred on 2022-11-12
Really need to see your configuration.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

While I prefer ppa since it is updated more frequently than the ISO, you can download the ISO and create a bootable flash drive. I believe it is based on Lubuntu.

---

### Post by jukingeo on 2022-11-13
> **dragonfly41 said:**
> Have you searched for threads discussing the original error message ..

*x86 CPU: SGX disabled by bios.*

[https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04](https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04)

Yes, I looked into that initially, but quickly found out that my BIOS doesn't have a SGX setting.   In digging for a work around, I had found out that this message comes up every time on boot and the computer boots anyway.  I know this because it happens on my wife's computer.  So doing some further digging, I found out that it was a booting issue.   I might have jumped to the wrong conclusion when I had reinstalled Ubuntu 22.04, but I was dismayed that while it solved one issue, it created another which was the the fact that Grub is going into the recovery mode.   So everything is now pointing to Grub.

The reinstall of Ubuntu works, but I can only get to it by manually selecting the drive from the boot menu.  Not really an ideal situation.  What I don't get is why didn't the reinstall obliterate the old Grub and install a fresh one?

> **oldfred said:**
> Really need to see your configuration.

How would I go about that?

> 
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

While I prefer ppa since it is updated more frequently than the ISO, you can download the ISO and create a bootable flash drive. I believe it is based on Lubuntu.

Okay, but that will take a bit.  Are there any other programs like Boot-Repair?  Perhaps there is something more robust that doesn't care what the drive system is?  I don't remember having to go through all this in the past.  I was able to use the Live CD (or USB) to fix Grub.  

Thanks,
Geo

---

### Post by jukingeo on 2022-11-14
I had no idea what happened, I had posted the pastebin link last night and for some reason the post didn't show up.

Well, here it is again:

[http://paste.ubuntu.com/p/zNz8NhnGqr/](http://paste.ubuntu.com/p/zNz8NhnGqr/)

---

### Post by yancek on 2022-11-15
Line 5 of boot repair shows you have Grub installed to the MBR of sda while Ubuntu is installed on partition sdb1, a second drive.  Beginning at line 25, it shows an EFI partition with both grub and windows proper EFI files.  If you are booting in Legacy/CSM mode, you don't need or use that partition.  Boot repair shows windows 7 on sda3 and Vista on sdb2 and sdc1.  Is that correct?  Vista and windows 7 were generally installed in Legacy mode.  I don't think Vista can be booted UEFI but 7 can though EFI is not the default.  Line 115 shows sda is a GPT drive so that windows on sda3 would need to be EFI.  Windows won't boot from a GPT drive unless it is EFI.

Beginning at line 99, you see the EFI boot entries from the BIOS EFI firmware which does not include an entry for Ubuntu.  Line 131 shows the /etc/fstab file has no EFI entry which it should show, sda1 should be mounted at    /boot/efi.  

Have you tried the suggested repair at the end of the boot repair output?  It should create and EFI entry for Ubuntu in the BIOS firmware and have the EFI/Ubuntu files on sda1 (EFI partition) pointing to Ubuntu on sdb1 and create the /boot/efi entry for sda1 in the /etc/fstab file.  I would think that doing this would enable EFI boot of both Ubuntu and windows 7 but will not boot vista from Grub.  If you have tried this, what was the outcome?

---

### Post by oldfred on 2022-11-15
I have seen several cases where Boot-Repair now has not correctly seen the Windows version. Particularly with Windows 11.

Since Windows is installed in UEFI mode, best to make sure Ubuntu is installed in UEFI mode.
Windows requires gpt partitioning for UEFI boot and has since Windows 8 released in 2012 for all installs by vendors. Users could still use BIOS/MBR for old systems.

Ubuntu will let you install in UEFI boot mode to MBR(msdos) partitioned drives, but probably should not. So sdb could be either UEFI or BIOS install. It actually looks like both at come point since you have the BIOS boot version of grub in MBR and UEFI version of grub in ESP on sda. One one of those grubs will work, normally, so you have to have grub installed to boot in same mode as UEFI/BIOS is set to boot.
How you boot install media UEFI or BIOS is then how it installs or repairs.

Windows on sdc with MBR must be BIOS boot? 

It sounds like you had both versions of grub installed and on reboot chose incorrect one from UEFI boot menu or changed UEFI boot settings to boot in wrong mode.

Best to have all systems in same boot mode. And Windows drives which mode you install Ubuntu. If Windows is UEFI, you need Ubuntu in UEFI boot mode. With multiple drives, you technically can have installs one each drive in different mode. But then cannot use grub to boot other installs, only UEFI boot menu. If installs are on same drive, they must be in same boot mode.

Longer term, you need to convert sdb & sdc to gpt. But that normally erases entire drive, so you need good backups.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by jukingeo on 2022-11-15
Hello,

As I answer your message below, keep in mind, I don't have a Pastbin account and as such, I have NOT viewed the file.


> **yancek said:**
> Line 5 of boot repair shows you have Grub installed to the MBR of sda while Ubuntu is installed on partition sdb1, a second drive.

Yes, that is correct

 >  Beginning at line 25, it shows an EFI partition with both grub and windows proper EFI files.  If you are booting in Legacy/CSM mode, you don't need or use that partition.  Boot repair shows windows 7 on sda3 and Vista on sdb2 and sdc1.  Is that correct?  Vista and windows 7 were generally installed in Legacy mode.  I don't think Vista can be booted UEFI but 7 can though EFI is not the default.  Line 115 shows sda is a GPT drive so that windows on sda3 would need to be EFI.  Windows won't boot from a GPT drive unless it is EFI.

I only EVER had Windows 7 on my machine.  I have no idea why it sees Vista.  It could be at one point I had Windows XP on the drive, but it was replaced with Windows 7.  The rest of what you wrote with EFI UEFI, GPT is roaring over my head like a jet engine.

Beginning at line 99, you see the EFI boot entries from the BIOS EFI firmware which does not include an entry for Ubuntu.  Line 131 shows the /etc/fstab file has no EFI entry which it should show, sda1 should be mounted at    /boot/efi.  

> Have you tried the suggested repair at the end of the boot repair output?  It should create and EFI entry for Ubuntu in the BIOS firmware and have the EFI/Ubuntu files on sda1 (EFI partition) pointing to Ubuntu on sdb1 and create the /boot/efi entry for sda1 in the /etc/fstab file.  I would think that doing this would enable EFI boot of both Ubuntu and windows 7 but will not boot vista from Grub.  If you have tried this, what was the outcome?

As I said above, I couldn't view the file.   What I would like to know at this point is how to fix this mess and going a step further, how did my son's key presses managed to cause this.

Thank you.

---

### Post by QIII on 2022-11-15
paste.ubuntu.com can be accessed using your Ubuntu One SSO -- the very same user and password you use to log in to the Ubuntu Forums.

---

### Post by jukingeo on 2022-11-15
> **oldfred said:**
> I have seen several cases where Boot-Repair now has not correctly seen the Windows version. Particularly with Windows 11.

Since Windows is installed in UEFI mode, best to make sure Ubuntu is installed in UEFI mode.
Windows requires gpt partitioning for UEFI boot and has since Windows 8 released in 2012 for all installs by vendors. Users could still use BIOS/MBR for old systems.

Ubuntu will let you install in UEFI boot mode to MBR(msdos) partitioned drives, but probably should not. So sdb could be either UEFI or BIOS install. It actually looks like both at come point since you have the BIOS boot version of grub in MBR and UEFI version of grub in ESP on sda. One one of those grubs will work, normally, so you have to have grub installed to boot in same mode as UEFI/BIOS is set to boot.
How you boot install media UEFI or BIOS is then how it installs or repairs.

As I was explaining to yancek above all this UEFI MBR, GPT stuff is starting to go over my head.  Really, all I want to know is how to fix it because I can't even fix Grub the old fashioned way (obliterate it and install new) at this point.

> Windows on sdc with MBR must be BIOS boot? 

I prefer it that way so this way my sons can't access Windows directly.   However, I want the computer to boot directly into Ubuntu 22.04.   As of yesterday, I had tried to fix it with the USB version of Boot Repair (which was one of your links).  Now Ubuntu doesn't work anymore either.  So I am only working on Windows.

> It sounds like you had both versions of grub installed and on reboot chose incorrect one from UEFI boot menu or changed UEFI boot settings to boot in wrong mode.

Well, for the longest time I had Ubuntu 16.04 on my machine and never upgraded from that as it is always a major hassle.   So I went right from 16.04 to 22.04, but the install was done on a new hard drive.

> Best to have all systems in same boot mode. And Windows drives which mode you install Ubuntu. If Windows is UEFI, you need Ubuntu in UEFI boot mode. With multiple drives, you technically can have installs one each drive in different mode. But then cannot use grub to boot other installs, only UEFI boot menu. If installs are on same drive, they must be in same boot mode.

Okay, so if that is what is wrong, then what does one do to fix it.   I use Gparted to setup and format the hard drives and there is NO mention of UEFI GPT or what have you.  The choices are NTFS FAT32, EXT3 or EXT4.

> Longer term, you need to convert sdb & sdc to gpt. But that normally erases entire drive, so you need good backups.

Backing those drives up is not a problem.  The only issues is the main C drive which is sac.  That cannot be touched as that is the Windows drive.   Now the only problem is HOW to change the drives over.  THat I don't know how to do.


Thanks for the helps so far, but I am hoping you can tell me of a resolution soon.

Geo

---

### Post by oldfred on 2022-11-15
Windows 7 could be installed in UEFI boot mode. but not with UEFI secure boot on.
Microsoft required vendors to install Windows 8 in UEFI boot mode only to gpt partitioned drives.

UEFI [URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface"]https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface
[/URL]MOK - Machine Owner Key (MOK) [https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)
ESP/efi -  Efi System Partition for UEFI boot on gpt drive:  [https://en.wikipedia.org/wiki/EFI_System_partition]("http://en.wikipedia.org/wiki/EFI_System_partition")
bios_grub - For BIOS boot on gpt drive: [https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)     
BIOS - Basic Input/Output System [https://en.wikipedia.org/wiki/BIOS]("http://en.wikipedia.org/wiki/BIOS") # must be inside first 2TB of drive
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
Some vendors in 2020 are announcing CSM will be eliminated. Systems will be UEFI Class 3 (no CSM).
 Secure Boot - [https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [https://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")
MBR(msdos) [https://en.wikipedia.org/wiki/Master_boot_record]("http://en.wikipedia.org/wiki/Master_boot_record")

---

### Post by yancek on 2022-11-16
>   I have no idea why it sees Vista. 

I don't know how boot repair determines the version of windows on a partition but I have seen other posts where it was incorrect.  It isn't really pertinent to your problem.

>  The rest of what you wrote with EFI UEFI, GPT is roaring over my head like a jet engine. 

If you are going to continue to use computers, you will need at least a basic understanding of what UEFI is and the differences between it and Legacy installs.  The last compputer I bought 2 years ago ins/t capable of booting in Legacy mode but only UEFI and that is the way the industry is going.  The link below gives a brief description of it and if that isn't detailed enough you should be able to easily find more detailed explanations.

[https://www.techtarget.com/whatis/definition/Unified-Extensible-Firmware-Interface-UEFI](https://www.techtarget.com/whatis/definition/Unified-Extensible-Firmware-Interface-UEFI)

>  I had tried to fix it with the USB version of Boot Repair (which was one of your links). 

Does that mean you tried the repair suggested in the boot repair output of reinstalling Grub in EFI mode?  If so, what happened?  Did you get any messages indicating success or failuere?

Are you able to boot windows on sdc and which version of windows is it, 7?  Do you boot it by selecting that drive in the BIOS?

>    So I went right from 16.04 to 22.04, but the install was done on a new hard drive. 

It appears you installed Ubuntu on the new drive (sdb) in UEFI mode but since there was no EFI partition on that drive, it installed the EFI files on sda.  THe Grub code in the MBR of sda is most likely from your old 16.04 install.  Can you disable Legacy/CSM boot in the BIOS firmware and try booting?  Have you done this already?

If you tried the boot repair suggestion and it failed, I would try reinstalling Ubuntu onto sdb after creating an EFI partition on that drive.  If possible, disconnect or disable sda and sdc.

---

### Post by jukingeo on 2022-11-17
> **oldfred said:**
> Windows 7 could be installed in UEFI boot mode. but not with UEFI secure boot on.
Microsoft required vendors to install Windows 8 in UEFI boot mode only to gpt partitioned drives.

I have Windows 7 on the main C drive, I don't have Windows 8, nor do I intend to use it.


> 

UEFI [URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface"]https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface
[/URL]MOK - Machine Owner Key (MOK) [https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)
ESP/efi -  Efi System Partition for UEFI boot on gpt drive:  [https://en.wikipedia.org/wiki/EFI_System_partition]("http://en.wikipedia.org/wiki/EFI_System_partition")
bios_grub - For BIOS boot on gpt drive: [https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)     
BIOS - Basic Input/Output System [https://en.wikipedia.org/wiki/BIOS]("http://en.wikipedia.org/wiki/BIOS") # must be inside first 2TB of drive
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
Some vendors in 2020 are announcing CSM will be eliminated. Systems will be UEFI Class 3 (no CSM).
 Secure Boot - [https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [https://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")
MBR(msdos) [https://en.wikipedia.org/wiki/Master_boot_record]("http://en.wikipedia.org/wiki/Master_boot_record")

Ok, I am going to be frank and don't really want to be inundated with the technical jargon behind how the storage system works on hard drives,  I just would like the fastest and easiest way to fix my issue so I can have my computer boot into Ubuntu again.  So cutting to the chase, which one of those links will tell me how to do that?  ....preferably step by step.

Thanks,
Geo

---

### Post by jukingeo on 2022-11-17
> **yancek said:**
> I don't know how boot repair determines the version of windows on a partition but I have seen other posts where it was incorrect.  It isn't really pertinent to your problem.

Yeah, it probably is incorrect as I never had Vista on my system.  I intend to keep Windows 7 for a VERY long time.

> 
If you are going to continue to use computers, you will need at least a basic understanding of what UEFI is and the differences between it and Legacy installs.  The last compputer I bought 2 years ago ins/t capable of booting in Legacy mode but only UEFI and that is the way the industry is going.  The link below gives a brief description of it and if that isn't detailed enough you should be able to easily find more detailed explanations.

[https://www.techtarget.com/whatis/definition/Unified-Extensible-Firmware-Interface-UEFI](https://www.techtarget.com/whatis/definition/Unified-Extensible-Firmware-Interface-UEFI)

All these terms are very Greek to me and they differ from what I am used to seeing in partitioning programs.   I have been using Gparted for a while now and it sets up the drive with FAT32, NTSC, EXT3 or EXT4.  I know the first two are for Windows partitions and the latter two are for Linux.  There is nothing that says if I want to set up my hard drives in UEFI mode, or Legacy mode.   So in all, I don't know how things got messed up and further why no one can tell me that how everything worked fine until my son hit some key combination in a game that somehow managed to obliterate Grub.   Now, I can't even reinstall it!

> 
Does that mean you tried the repair suggested in the boot repair output of reinstalling Grub in EFI mode?  If so, what happened?  Did you get any messages indicating success or failuere?

In one of the links Old Fred sent me, it was an iso for Boot Repair.  So I downloaded that, made a bootable USB and tried to fix Grub / MBR on drive c with that.   It failed.

> Are you able to boot windows on sdc and which version of windows is it, 7?  Do you boot it by selecting that drive in the BIOS?

Yes.  It is Windows 7 64-bit Home Version, but it isn't on the c drive, it is on the a drive and I boot into it from the boot menu.  In fact that is how I am using my machine now since the Windows partition is working.   I USED to have Ubuntu 16.04 on the drive alongside Windows and initially it was dual boot through Grub, but as my luck has it, Grub became corrupted with that install.   I divided the drive into two bootable portions so I could get into Windows outside of Grub.   I fixed Ubuntu  16.04 and Grub and that booted directly into 16.04.   So that was the way my C drive or sda drive was set up.

When I installed Ubuntu 22.04, I had put it on a new partition on the d drive or sdb1 and that worked fine.  Once I knew everything was working in Ubuntu 22.04, I had deleted 16.04 off of the C drive and expanded the Windows partition to the full size of the drive.

> 
It appears you installed Ubuntu on the new drive (sdb) in UEFI mode but since there was no EFI partition on that drive, it installed the EFI files on sda.

While it is the D drive in Windows, it is the 2nd drive in Ubuntu and the 1st partion  (sda).  I have allotted 500gig to Ubuntu 22.04 and the rest is just storage.

>   THe Grub code in the MBR of sda is most likely from your old 16.04 install.

The boot loader is on the main C drive, so yeah, 16.04 was originally there, but wouldn't have the install of 22.04 deleted the old version of Grub and installed a new one?  At least that is what it looked like to me.

 >  Can you disable Legacy/CSM boot in the BIOS firmware and try booting?  Have you done this already?

I am not sure.  No, I haven't tried that before.

If you tried the boot repair suggestion and it failed, I would try reinstalling Ubuntu onto sdb after creating an EFI partition on that drive.  If possible, disconnect or disable sda and sdc.[/QUOTE]

Ubuntu 22.04 is already on the sdb drive. And how do you create an EFT partition with Gparted?  I don't recall seeing that as an option.

Again, I will reiterate what I said earlier.  I am most interested in the easiest and fastest way to rectify the issue and one that will not obliterate my Windows partition.  If I have to continue to boot that through the boot menu, I am fine with that.  I want the default OS to load up to be Ubuntu anyway.

Thanks,
Geo

---

### Post by jukingeo on 2022-11-17
Hello guys, I figured I would show you the information in what Grub does upon straight boot up:

Error:  No Such Device:  2d527b58-c0e4-4e6c-b3b4-cbdb52f8ebc8c
Error:  Unknown File System

Entering Rescue Mode

grub rescue> _ (blinking cursor)


I am not sure if that tells you anything, but that is what is happening on boot up when I say that it goes into "grub rescue".   I figured it would have been simple to just over write grub with a reinstall of Ubunut 22.04, but that didn't work.

---

### Post by yancek on 2022-11-17
>  Hello guys, I figured I would show you the information in what Grub does upon straight boot up:


The above from your last post which shows what you posted below:  That shows the device UUID, the 32 characters displayed after it.  That means Grub is looking for the partition with that UUID and cannot find it.  You can find the UUID of each partition on the computer of all drives connected when you run the command:  blkid  THis information is shown in the boot repair output you posted earlier beginning at line 192.  Ubuntu is installed on sdb1 and on line 200 it shows the UUID for that partition.  It is not the same as the one you posted.  If you cannot see your boot repair output, run blkid and check the partition UUID for sdb1.  If it is not the same as the UUID you posted from the error message, that could be the problem or part of it at least.

>  Error:  No Such Device:  2d527b58-c0e4-4e6c-b3b4-cbdb52f8ebc8c

Since you cannot boot the installed Ubuntu, boot the USB you used to install it and mount sdb1.  Look in /boot/grub/grub.cfg for the menuentry for Ubuntu and also look in /etc/fstab on sdb1 for the entry for the system partition ( / ).  The entry should begin with # / was on /dev/sdb1 ... with the UUID on the line below.  If the UUID you got from blkid for sdb1 is not the same as the UUID in your error message, replace it with what you got from blkid in both grub.cfg (do NOT update Grub) and /etc/fstab, save the files and reboot to test.  Make a note of what you did so if it fails, we know that is not the entire problem.  

You might look in grub.cfg to see if there is an entry for windows and what it is.  Since you can boot windows 7 and as I understand it, 7 is on device sdc, you probably won't be able to boot it from Grub as Ubuntu seems to be installed in UEFI mode.

---

### Post by oldfred on 2022-11-17
Your sda drive has Windows in UEFI mode. Is that really the Windows that boots?
As the Windows in sdc does not show the typical BIOS boot files.

Then you have UEFI system, with UEFI install of Windows using gpt partitioning.
It looks like at least one install of Ubuntu was UEFI as you show UEFI version of grub.

If Windows is booting in UEFI mode, you need to reinstall grub in UEFI boot mode.
Just use Boot-Repair booted in UEFI mode and reinstall grub.

---

### Post by jukingeo on 2022-11-17
> **oldfred said:**
> Your sda drive has Windows in UEFI mode. Is that really the Windows that boots?
As the Windows in sdc does not show the typical BIOS boot files.

Windows is using its own bootloader.  I had a problem a while back when I loaded Ubuntu 16.04 and that was when I upgraded Windows XP to Windows 7.  It had put it's own boot loader on but it never could boot on its own.  I always HAD to go into the boot menu to boot.  I was/am fine with that.

> 
Then you have UEFI system, with UEFI install of Windows using gpt partitioning.
It looks like at least one install of Ubuntu was UEFI as you show UEFI version of grub.

If Windows is booting in UEFI mode, you need to reinstall grub in UEFI boot mode.
Just use Boot-Repair booted in UEFI mode and reinstall grub.

Ok, I tried that making sure I used the UEFI version and (low and behold) it didn't work and now I have a new error message:
[I]
Locked NV-ram detected[/I]

and it spewed out a Pastebin file:

[http://paste.ubuntu.com/p/JQSYVfBmqx/](http://paste.ubuntu.com/p/JQSYVfBmqx/)

When I boot up the computer, this is what I get:

[I]Error: file '/boot/grub/i386-pc/normal.mod' not found

Enter Rescue Mode...

grub rescue> _[/I]


Ok, so at this point I am getting a bit perturbed about this.  I can't believe that a simple miskey press from my son managed to cause this.  Worse, it doesn't seem like what we are doing is fixing the issue.   So I have a few more questions.

1) On boot up it goes into Grub Rescue Mode.  Can't we fix the problem using that?
2) Since Grub isn't cooperating, can it be obliterated and a different boot loader be used.  One that is better and more robust?
3) Is there a way I can make the computer look to the sdb drive and make that the boot drive?
4) Can Ubuntu Studio 22.04 be set up to boot without Grub?

Finally, and I know I have asked this question a few times before.  How is it that a shift key / Windows key combination can brick the bootloader?  To me this is the most important thing ever as I don't want it to happen again.

Thanks
Geo

---

### Post by oldfred on 2022-11-18
> [I]
Locked NV-ram detected[/I]
That is your UEFI and is preventing update.

Many new UEFI have additional security. It sounds like you did an UEFI update & it restored defaults.
Not sure if you have an Administrator UEFI password set, or other specific settings that lock or prevent UEFI entries.
Some find resetting to defaults works, many have to review manual and see what setting may be causing the issue.
Found this not sure if helpful or not.
[https://www.linux.org/threads/solved-locked-nvram-detected-api-issue-on-reboot-elementary-and-mint.33256/](https://www.linux.org/threads/solved-locked-nvram-detected-api-issue-on-reboot-elementary-and-mint.33256/)

Some systems, mostly Acer require "trust" on UEFI settings. So update by installer does not work totally, but user has to go into UEFI settings and find the entry for "unknown" and change to Ubuntu and set trust on that entry.

---

### Post by jukingeo on 2022-11-22
> **oldfred said:**
> That is your UEFI and is preventing update.

Many new UEFI have additional security. It sounds like you did an UEFI update & it restored defaults.
Not sure if you have an Administrator UEFI password set, or other specific settings that lock or prevent UEFI entries.
Some find resetting to defaults works, many have to review manual and see what setting may be causing the issue.
Found this not sure if helpful or not.
[https://www.linux.org/threads/solved-locked-nvram-detected-api-issue-on-reboot-elementary-and-mint.33256/](https://www.linux.org/threads/solved-locked-nvram-detected-api-issue-on-reboot-elementary-and-mint.33256/)

Some systems, mostly Acer require "trust" on UEFI settings. So update by installer does not work totally, but user has to go into UEFI settings and find the entry for "unknown" and change to Ubuntu and set trust on that entry.

As far as I know, I didn't make any security settings to UEFI.  When it comes to that the BIOS on my system is VERY limited.  I bought the motherboard back in 2017, so it is a few years old and probably doesn't have the features as newer motherboards have.   In terms of settings, the ONLY ones I have set where that of GParted.  The options there are for the disk format, i.e.  NTFC, ext4, FAT32, etc.  I can set primary and secondary partitions and make the primary bootable, but there are NO settings for UEFI.

Since it seems as if the issue was being aggravated by my having an operating system on separate drives, I had went back to my original setup of having BOTH Windows and Ubuntu on the same drive, which is the sda drive.   Sadly this is only 500gig and I wanted to have 500 gig for Windows and 500 for Ubuntu.   Since I don't use many programs outside of what comes with the initial installation of Ubuntu Studio, as opposed to Windows, which I have quite a few programs, I have set up Ubuntu with only 150gig and the rest to Windows.   I then installed Ubuntu 22.04 with no Grub on the 150gig partition.....IT WORKED!    Yes, I have to use the F12 Boot Menu to get into Windows, but I had to do that before.  Ubuntu Studio will boot directly in (with no Grub menu) on power on, which is also what I wanted. 

Sadly though, I really wanted to have Windows have the full 500gig.  So as of now, I am NOT going to label this issue as 'solved' as the end result was not exactly what I was looking for.   However, I am at the state where I have a functional machine that I can boot the way I did prior to my son's mishap.

Now, I really don't understand what happened to cause this mess in the first place, so I am hesitant to let my son back on my machine to play games.   Since no one could tell me why a key combination pressing could obliterate my boot sector on my main drive, I am seeking an alternative solution.   Is there a way to block key combinations?  In other words when my son plays a game, I would like to disable shift, control, and windows keys functions.  Hopefully that would prevent this from happening again.

Thanks for your help up to now and even though the end result wasn't what I wanted, I have my machine functioning with both Windows and Ubuntu again.

Geo

---

