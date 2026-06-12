---
title: "GRUB won't load"
date: 2017-06-08
forum: General Help
---

### Post by michaloslav on 2017-06-08
So I recently installed Ubuntu on my pc and since then, I can't boot into anything. 
I started off by installing 17.04 on my second drive (I have windows installed on sda1 and now I installed Ubuntu on sdb3), but it wouldnt load. It just showed the regular "Loading operating system..." message, which stayed up for over an hour until I decided to restart it. Then at various points, I got into a booting loop with no sign of grub being there at all and the grub rescue menu (it gave me an unknown Filesystem error and also a no such device error). I tried to reinstall GRUB and run the boot-repair while booted from the installation USB which ran without any errors but didn't help at all. After reinstalling several times, I tried to format the partition again and install Ubuntu 16.04 LTD (maybe I got the version wrong, just the newest lts version). Again, just the "Loading operating system..." message. I don't know what to do anymore, I can't boot into either system now and the only thing I can do is boot into the USB. Pls help me. 

TLDR, just installed Ubuntu alongside Windows and can't boot into either one now.

---

### Post by Impavidus on 2017-06-08
As you already found boot-repair, could you post a link to the boot info summary?

---

### Post by michaloslav on 2017-06-08
Thanks for the reply. Here you go:
[https://paste2.org/sZHPD1jK](https://paste2.org/sZHPD1jK)

---

### Post by oldfred on 2017-06-08
You have Windows installed in BIOS boot mode on sda, but grub in MBR. You need to change that to be a Windows boot loader.
Boot-Repair may do it, but it also looks like you left Windows hibernated, so the Linux NTFS driver cannot correctly see it. You may need your Windows repair flash drive to fix it.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

You have grub installed everywhere, which is the default by Boot-Repair. 
Better to only have grub installed to sdb. You can still use Boot-Repair but have to use Advanced options, choose operating system and choose drive to install boot loader into (sdb). Then set BIOS to boot sdb.
If Windows is hibernated, grub probably will not find it, and will not boot it. And Windows updates often re-set to defaults turning on fast start up/hibernation. Then you can still boot from MBR of sda, by using BIOS boot menu often f10 or f12 or reset order in BIOS. After turning fast start up back off you can reset to boot sdb again.
       
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

 You show sdb3 as ext3, but with ESP - efi system partition flag. That cannot be. The ESP can only be FAT32 if you want to experiment with UEFI booting and have UEFI hardware. But often better just to have Ubuntu as BIOS as Windows is BIOS boot mode.

The grub in sdb looks like from a previous install, it is looking in wrong sector for reset of grub. It should refer to first sector of bios_grub partition.
Using Boot-Repair should fix that.

If hardware is newer UEFI based, do not turn on UEFI as systems are installed in BIOS/CSM/Legacy boot mode.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by michaloslav on 2017-06-08
Thank you so much. I did my best to use your advice but I still can't boot. Could you please check this new log and see what more can be done? Thanks again

[https://paste2.org/6yaDZcKN](https://paste2.org/6yaDZcKN)

---

### Post by oldfred on 2017-06-08
It looks like Boot-Repair says it installed grub to sdb. But sector is still not correct, it should be first sector of bios_grub partition.
It looks like you also have a separate /boot partition? Not shown in fstab? But grub menu entries show one UUID for boot and another for install. 
Generally best to not have separate /boot partition as it adds complications and is not normally required. But you have to totally reinstall grub if you want to revert to the /boot folder in / (root), not the /boot partition.

> Grub2 (v1.99-2.00) is installed in the MBR of /dev/sdb and looks at sector          1155962880 of the same hard drive for core.img, but core.img can not be 
         found at this location.

But did you run all the command it said to run like these from its log? Not sure this is all it requested.
>  Please type: sudo chroot "/mnt/boot-sav/sdb10" dpkg --configure -ansudo chroot "/mnt/boot-sav/sdb10" apt-get install -fynsudo chroot "/mnt/boot-sav/sdb10" apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
Then type: sudo chroot "/mnt/boot-sav/sdb10" apt-get install -y --force-yes grub-pc linux-generic 



And did you try to install a Windows type boot loader to sda? It looks like you have Windows 7,  and os-prober saw it, so Boot-Repair should offer to install a Windows type boot loader. Choose only sda.

Are you now getting grub menu, when booting from sda.
You also have nVidia, so probably need nomodeset until you install the proprietary nVidia driver from Ubuntu repository in System Settings, Software & Updates, drivers tab. Or if only able to use recovery mode (under advanced options in grub menu), then you have to use command line.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by michaloslav on 2017-06-09
So how do I fix the sector problem? Yes, I have a separate /boot partition, when I installed it, I read some articles online where they said that this was recommended. Should I remove it? 
I tried to run those commands but it didn't work. The first time, it told me that one of the locations is incorrect and now, it's just saying "dpkg: error: unknown option -n"
I tried to repair Windows from the CD and the first time, it seemed to work. I even got GRUB running and was able to boot into Ubuntu but now, I can't get to GRUB at all again. I tried to run the CD again but it told me that I had a different version of Windows from that of the CD. That is somewhat true, after I installed Windows, I wanted a higher edition (to do some changes that weren't possible in the original) so I got some pirated version of Windows running along with the regular one. Back before I started all of this Ubuntu stuff, it always asked me at start up whether I wanted to run Windows 7 or Windows 7 Loader XE. I'm guessing the CD now sees this different version and refuses to work.
Also, could you please either link to articles explaining how to do the things you're advising me to do or explain to me how to do it? I'm a total noob as far as Linux or GRUB goes so when you tell me the sector is wrong, I genuinely have no idea what to do about it. 
I tried to run boot repair again, here's the new log: 
[https://paste2.org/EKkFs3YW](https://paste2.org/EKkFs3YW)

---

### Post by oldfred on 2017-06-09
Grub defaults to install to sda, but that is your Windows drive. You want a Windows boot loader in sda.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

Probably best then to reinstall on sdb. 
With multiple drives, only use Something Else install option.
And since large drive, you have to use gpt partitioning.
I suggest having both an ESP - efi system partition as first partition, but in your case that would be for future use. Since Windows is BIOS you want Ubuntu in BIOS boot mode. And BIOS boot requires the bios_grub partition.

With newer UEFI hardware, how you boot install media UEFI or BIOS is then how it installs. So always boot in BIOS mode, unless you want to experiment with UEFI. If Windows is BIOS and Ubuntu UEFI you can only boot from UEFI  menu not from grub menu.

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader, you want to change from default of sda to drive that is sdb.
Some may show older versions of Ubuntu but install is identical, other than perhaps some minor visual changes.
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[URL="http://www.tecmint.com/ubuntu-14-04-installation-guide/"]http://www.tecmint.com/ubuntu-14-04-installation-guide/
[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 

[URL="http://www.tecmint.com/ubuntu-14-04-installation-guide/"]
[/URL] I prefer to use gparted to partition in advance.
      
 Then you still use Something Else to choose(change) the partitions you already have on sdb.
Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

       
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by michaloslav on 2017-06-09
Okay, I reinstalled Ubuntu just like you said but it still didn't work. Then I managed to get the Windows CD running again which did solve one of my problems. Now if I boot from sda, I can use Windows just like before. But if I boot from sdb, I get stuck on "Laoding operating system..." again. I tried deleting all the partitions I used for Linux, recreating them and reinstalling again but it didn't change anything. So I'm basically right where I started - I have Windows but don't have Ubuntu or GRUB. At least I can finally work which was the main problem but I'd still like to get Ubuntu to function. Is there anything else I could do?
Also, thank you for explaining things in such detail to me. I get that writing detailed instructions for idiots online probably isn't the most enjoyable activity and so I'm really grateful for all your help.

---

### Post by oldfred on 2017-06-09
Thanks, but a lot was copied & pasted from previous posts. :)

If you re-installed post a new link to a new copy of Summary report.
Are you installing with Something Else and specifying grub be installed to sdb? And Booted in BIOS mode, so it installs the BIOS version of grub. 

If you happened to boot in UEFI mode then grub will error out an not install and old copy of grub in MBR of sdb will not be updated.

---

### Post by michaloslav on 2017-06-09
Yes, I made sure to install with Something Else and to have it on sdb. To be honest, I'm not sure how to boot in UEFI but I'm assuming that my PC always boots in BIOS mode. Should I check it somehow? (I have Gigabyte P67A-D3-B3 F7)
[https://paste2.org/3CBOOPnw](https://paste2.org/3CBOOPnw)

---

### Post by oldfred on 2017-06-09
From your MBR & fdisk.
      ```
 Grub2 (v1.99-2.00) is installed in the MBR of /dev/sdb and looks at sector 

 [COLOR=#ff0000]1156986880[/COLOR] of the same hard drive for core.img, but core.img can not be  

 found at this location.
/dev/sdb4 [COLOR=#ff0000]5,451,954,176[/COLOR] 5,451,958,271 4,096 BIOS Boot partition     

```

It is saying grub installed correctly error 0 means no reported error.
But those two numbers do not match. MBR should be finding core.img starting at first sector of bios_grub partition.

Lets try this. 
Shrink sdb1 by 2 MB. You may never use that. Windows adds that to gpt drives before any NTFS partition.
And then create a new unformatted 1MB partition and assign bios_grub. Delete sdb4.
Check that BIOS has sdb set for AHCI.
The reinstall grub like you just did.
And run report to see if sectors match.

Grub used to have an issue with drives over about 600GB, but that was fixed years ago. And supposedly bios_grub can be anywhere on drive.

Since you only have BIOS installs, I would not worry about UEFI. 
Your system looks like it may have UEFI but it would be an early version.

---

### Post by michaloslav on 2017-06-10
How exactly can I shrink the sdb1 partition? I tried it in GParted, Disks and Disk Management in Windows, I can't resize it. I'm guessing it's because it's unformatted although it's hard to be sure. The only thing I can do is delete it completely but I don't think that's a good idea.

---

### Post by oldfred on 2017-06-10
Are you using live installer?
I would think you can move, edit formatted partitions, but have not tried.

The Windows system reserved required by Windows before the first NTFS partition on a drive.
But I think it only really is required before the first system install. With BIOS/MBR Windows would write data into the sectors after the MBR like flexnet DRM rights management security codes. And grub writes core.img into the sectors after the MBR. And originally the conflicted, but grub did a work around.
But with gpt there are no sectors after the gpt protective MBR. So grub has bios_grub partition for core.img and Windows has its system reserved to use for misc somewhat hidden info.
If NTFS partition on sdb is not an install, just a data partition, then you should not even need it. I have seen many users with NTFS data partitions on additional large drives, but partitioned with gparted which does not auto add system reserved.
Or I think  you can just delete it, if that is only option. 

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by michaloslav on 2017-06-10
I used GParted from the installation USB. And yeah, I can move/edit/whatever basically any partition on any disk except for this one and also the bios_grub one. The only thing these two seem to have in common is that they're unformatted so I'm guessing that's the problem.

I did a bit of googling around and it seems like I should be able to safely delete the partition but I'm not sure and I'm kinda scared it'll **** things up. Are you sure it won't cause a ton of damage if I just delete it? And it should probably be reversible by just running the Windows repair CD, right?

---

### Post by oldfred on 2017-06-10
You can always delete & recreate as new unformatted partition.
When you recreate just be sure to right click and set boot parameter so seen as System Reserved. Not sure what gparted calls it.

Or format to just about anything, edit and change format to unformated after resize.
It should not have any data in it, and I do believe you can delete it. Just the one that would be before a NTFS partition on a gpt drive booting in UEFI mode is normally required. But I have seen installs without one that at least initially worked. Only if Windows wanted to save some data into it would then there be an issue.

---

### Post by michaloslav on 2017-06-10
Okay, I deleted sdb1 and used the space to make a new partition with the bios_grub flag on it (128 MiB is probably way too much for this but whatever, it shouldn't cause any problems). Then I ran boot-repair on it but I still can't boot. I just got a "no device connected" error or something like that. Any idea what to do with it?
[https://paste2.org/620U4pKv](https://paste2.org/620U4pKv)

---

### Post by oldfred on 2017-06-10
The bios_grub only needs to be 1 or 2MB. And only 2 with some other formats for / (root) partitions.
Your BIOS & bios_grub first partition now match.

Your errors are just like the old BIOS and IDE limits of 137GB. Those very old systems had to have all boot file inside the first 137GB of the drive.
I wonder if your system just does not support very large drives?
But I have not seen a newer UEFI based system have those type of issues.

Is the error from BIOS/UEFI or from grub?
If you hold shift key from BIOS, do you get grub menu or is error before that and from BIOS.
You need grub menu to add nomodeset because of nVidia card.

---

### Post by michaloslav on 2017-06-11
I don't think the problem is that the drive's too big although admittedly, I'm not sure. I know that some time ago (like 5 years ago) I installed Ubuntu and GRUB and it all worked fine. Back then, I had just sda which is 1TB whereas now I have that 3TB sdb drive. (I was just a dumb kid back then and I couldn't even learn how to use a new OS so I ended up uninstalling pretty quickly.) So it is possible that the size of sdb is the problem but in that case, I'm not sure what to do about that.

I'm guessing it's from grub, it always says "Loading operating system...", then it gives me an error (unknown file system/no such device/no device connected) and then it enters grub rescue.
Shift key doesn't do anything on boot for me so I can't really test anything that way.

---

### Post by oldfred on 2017-06-11
Now that it matches, I do not know why it will not boot.
It still may be some setting in UEFI/BIOS? But not familiar with your specific system to know.
I normally had to change some settings with older BIOS system, a lot more with my Asus UEFI system, and a few with my Gigabyte UEFI system.

If you are getting grub rescue then you are into grub and past BIOS.

See if this will boot your system. It is a small download. But follow its directions for copying to a flash drive. Some tools may not work as they only assume Ubunutu's hybrid ISO/flash drive configuration for ISO and use dd, which does not work for a lot of other ISOs.
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by michaloslav on 2017-06-11
Alright, I downloaded it and booted into it but it didn't seem to do much. I just found out that apparently, GRUB can't detect some files and that may be the problem. I took some pictures, some are a little blurry but I hope you can read it.
[https://drive.google.com/drive/folders/0BxEx7SS72gPdRl9obDdmaDN1Nzg?usp=sharing](https://drive.google.com/drive/folders/0BxEx7SS72gPdRl9obDdmaDN1Nzg?usp=sharing)

---

### Post by oldfred on 2017-06-11
You want to boot from sdb, so whatever is on sda, ignore.It looks like it shows a live image or ISOimage files. 

Does core.img or grub.cfg entries then work? From last image?

---

### Post by michaloslav on 2017-06-12
Nope, it says there's no file detected. I put a pic of it into that Google drive folder if you wanna look at it but it really just says no file detected. I'm guessing it's still somehow not looking into the right folder but I have no idea what to do about it.
(Sorry for the late replies BTW, times zones suck.)

---

### Post by oldfred on 2017-06-12
And is that the case with grub.cfg options also?

If just a brand new install, I might download a new ISO and verify it is valid.
And write to a different flash drive, using a different tool to create the flash drive.

Some have had issues installing with certain flash drives, certain ports on system, and which tool is used to create flash drive.
I can now (with lots of experience) install to existing ext4 partition with Something Else from my other hard drive (which makes it quicker) in about 10 minutes. A full install to a USB3 flash drive can take 30 minutes to even an hour, as write to flash drive is slow.

 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Also:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

      
 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by michaloslav on 2017-06-17
Nope, still the same. I've tried several ports, flash drives and installation tools. I also re-downloaded the package from the website, still the same thing. It usually gives me the "Unknown filesystem" error now, maybe that's something that could be addressed but I don't know how

---

### Post by oldfred on 2017-06-17
Is error still from your install or now from the installer?
Is BIOS set to AHCI for drives, not IDE nor RAID?

---

