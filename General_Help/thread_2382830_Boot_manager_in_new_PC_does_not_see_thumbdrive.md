---
title: "Boot manager in new PC does not see thumbdrive"
date: 2018-01-17
forum: General Help
---

### Post by AbleTassie on 2018-01-17
I was given a brand new PC in the last few weeks that has Windows 10 as the OEM OS. I really don't like Windows much anymore and would like to dual boot Lubuntu and Windows with the new PC. I have a thumbdrive with Lubuntu 16.04.3 LTS on it with persistence that I am presently using on an older PC that is about 7-10 years old (I think). In fact I am using the older PC and thumbdrive right now to ask this question.

I would like to do two things with the new computer. **First** I want to install Lubuntu on the hard drive of the new PC and I want to do it off the USB port if possible. **Second**, I want to use the new PC to boot off the USB into a Lubuntu OS with persistence. **Third**, if possible, I would like to be able to use the same thumbdrive to boot into Lubuntu with both the old and new PC.

PROBLEM: I can get into the boot manager by pressing F12 with the new PC, but the new PC does not see the present thumbdrive that I have with Lubuntu 16.04.3 LTS with persistence on it. It only gives me one option: to boot into the HD. So I am thinking the thumbdrive is not formatted in a way that the new boot manager can see the thumbdrive.

QUESTION: What can I do to solve this problem and do the three things described above that I would like to do?

Thanks,

A.

---

### Post by oldos2er on 2018-01-17
Assuming your new computer uses UEFI, you need to disable Secure Boot.

---

### Post by AbleTassie on 2018-01-17
Hello oldos2er,

I kind of figured what you are saying, but for some reason, when I go into the BIOS or Setup Utility, I cannot maneuver down to the Secure Boot Mode item using the vertical arrows to select it and disable it. So I may have to call tech support or consult a forum for this particular PC.

Thanks,

A.

---

### Post by C.S.Cameron on 2018-01-17
If secure boot is not the problem, you could use mkusb, (with default settings), to make the flash drive.
It works with BIOS and UEFI.

---

### Post by AbleTassie on 2018-01-18
Thanks, I will let you guys know what happens.

A.

---

### Post by AbleTassie on 2018-01-20
Hello everybody,

 I have disabled secure boot in my brand new PC. And I made a live boot Lubuntu 16.04.2 LTS thumbdrive using StartupDiskCreator and the PC recognizes the OS and boots into it. I did a temporary trial Lubuntu installation, rather than the full HDD installation. **This is a brand new computer given to me as a gift that has an OEM copy of Windows 10 on it.** Before I proceed with the full HDD install of Lubuntu I want to ask a couple of questions:

**1)** I remember that in the past I was given the option to install Lubuntu beside a preexisting Windows OS and could then dual boot on startup, choosing either Windows or Lubuntu. I still have that option, don't I? 

Can I set the BIOS or UEFI to make Lubuntu the default OS, so I don't have to choose Lubuntu every time on boot up?

**2)** I don't really like Windows that much any more, so I will probably not use it unless I have to. After I install Lubuntu can I later resize the Windows partition on the HDD relatively easily, using, for example, G-parted?

Thanks,

A.

 P.S. A while ago, I had a previously downloaded a Lubuntu 16.04.2 LTS amd 64 iso file for which I had checked the SHA256SUM and CheckSUM  and these SUMs were OK.

---

### Post by C.S.Cameron on 2018-01-20
Use Windows to shrink the Windows partition.
Use the Live USB to install Ubuntu.
I usually use the "Something else" option to partition the drive.
Do not check the Format box next to the Windows partition, (sda1).
Press "+" to add an ext4 partition for "/" the OS partition.
Add a partition for swap if you like.
The boot loader location should default to sda.
Lubuntu should end up as the first entry in the grub menu and will be the default option.
Windows will be toward the bottom of the grub menu but can be moved up.

---

### Post by yancek on 2018-01-20
I would also suggest using the 'Something Else' option which is a manual install and gives you some control.  It would also be a good idea to keep notes of the install steps in case of problems.  THe first link below gives a very brief explanation of installing Lubuntu with windows 10.  The second link below is the official Ubuntu documentation on dual booting with windows UEFI.  It has some information specific to installing Ubunt which won't apply but also some general principles on dual booting UEFI.

[https://www.lifewire.com/install-lubuntu-16-04-windows-10-4037894](https://www.lifewire.com/install-lubuntu-16-04-windows-10-4037894)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-01-20
What brand/model system?

Some require extra settings in UEFI and/or grub/kernel boot parameters.

See also link in my signature.

---

### Post by AbleTassie on 2018-01-20
> **oldfred said:**
> What brand/model system?

Some require extra settings in UEFI and/or grub/kernel boot parameters.

See also link in my signature.

Thanks to everybody, I have installed Lubuntu a few years ago (after Windows was already installed) for dual booting. But it's been a while. So I don't want to make a miss step: it could be costly. 

Regarding make and model: Acer Aspire E5-575 with Windows 10. 

**A couple final questions: **

**QUESTION # 1:** How easy is it to uninstall Lubuntu with a Windows 10 dual boot? (I may, for example, want to install Lubuntu 18.04 LTS when it comes out at the end of April this year. Or there may be another reason to uninstall Lubuntu, I'm not sure.)

Some procedures for uninstalling Ubuntu with a Windows 10 seem to require a Windows Installation DVD. I do not have a Windows Installer DVD or anything like that. I'm not sure one came with the PC. The PC is a gift. Should I try to find out if there was such a DVD that came with the PC?

**QUESTION #2: **Since I was able to live boot my new Acer PC from the USB drive after making the live boot usb with StartUpDiskCreator, do I really need to use mkusb or a compicated procedure to make a Lubuntu Live Boot USB with persistence? I have made such a live boot with persistence before without using mkusb. I am concerned that using mkusb may be too complicated.

Thanks,

A.
[h=1][/h]

---

### Post by C.S.Cameron on 2018-01-20
You should not need to uninstall Lubuntu when upgrading, you can do an upgrade from a running system or you can reinstall over the old Lubuntu installation, Just do not check the format box next to the Windows partition and it should be safe enough.
Some people prefer to also make a /home partition that can be reused over multiple installs.

You can download the Windows 10 ISO from Microsoft for free: [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)

You do not need a persistent USB to install Lubuntu, that is what SDC was made for. Just boot the USB, select Install and when you get to partitioning select Something else. Do not mess with the Windows partition, use Windows to do that if it needs shrinking.

---

### Post by AbleTassie on 2018-01-20
> **C.S.Cameron said:**
> You should not need to uninstall Lubuntu when upgrading, you can do an upgrade from a running system or you can reinstall over the old Lubuntu installation, Just do not check the format box next to the Windows partition and it should be safe enough.
Some people prefer to also make a /home partition that can be reused over multiple installs.

You can download the Windows 10 ISO from Microsoft for free: [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)

You do not need a persistent USB to install Lubuntu, that is what SDC was made for. Just boot the USB, select Install and when you get to partitioning select Something else. Do not mess with the Windows partition, use Windows to do that if it needs shrinking.

Thanks C.S. Cameron,

Do I need a PC serial number that has Windows 10 as an OEM feature to download the ISO file?

I am interested in making a Lubuntu usb thumbdrive with persistence to boot into Lubuntu when I am using the PC with public WiFi to protect the HDD. Do I need to use mkusb to make such a Lubuntu usb thumbdrive with persistence in order for the the UEFI or BIOS on this new PC to boot using the thumbdrive? 

Do you have any comments about the ease of just plain uninstalling Lubuntu if I want to?

Thanks,

A.

---

### Post by C.S.Cameron on 2018-01-21
From MS:
Using the tool to upgrade this PC to Windows 10 (click to show more or less information)

Here&#8217;s when to use these instructions:

    You have a license to install Windows 10 and are upgrading this PC from Windows 7 or Windows 8.1.
    You need to reinstall Windows 10 on a PC you&#8217;ve already successfully activated Windows 10.

If you are installing Windows 10 on a PC running Windows XP or Windows Vista, or if you need to create installation media to install Windows 10 on a different PC, see Using the tool to create installation media (USB flash drive, DVD, or ISO file) to install Windows 10 on a different PC section below.

Note: Before you install Windows 10, check to make sure your PC meets the system requirements for Windows 10. We also recommend going to the PC manufacturer's website for any additional info about updated drivers and hardware compatibility.

    Select Download tool, and select Run. You need to be an administrator to run this tool.
    On the License terms page, if you accept the license terms, select Accept.
    On the What do you want to do? page, select Upgrade this PC now, and then select Next.

    After downloading and installing, the tool will walk you through how to set up Windows 10 on your PC. All Windows 10 editions are available when you select Windows 10, except for Enterprise edition. For more information on Enterprise edition, go to the Volume Licensing Service Center.
        If you don't have a license to install Windows 10 and have not yet previously upgraded to it, you can purchase a copy here: [https://www.microsoft.com/en-us/windows/get-windows-10](https://www.microsoft.com/en-us/windows/get-windows-10).
        If you previously upgraded to Windows 10 on this PC and you&#8217;re reinstalling it, you don&#8217;t need to enter a product key. Your copy of Windows 10 will automatically activate later using your digital license.
    When Windows 10 is ready to install, you&#8217;ll see a recap of what you&#8217;ve chosen, and what will be kept through the upgrade. Select Change what to keep to set whether you would like to Keep personal files and apps, or Keep personal files only, or choose to keep Nothing during the upgrade.
    Save and close any open apps and files you may be running, and when you&#8217;re ready, select Install.
    It might take some time to install Windows 10, and your PC will restart a few times. Make sure you don&#8217;t turn off your PC.

I suggest mkusb if you want more than 4GB persistence and a Linux/Windows data partition. 
The latest UNetbootin will work with UEFI and BIOS if a max 4GB casper-rw file is suitable, you can also add a max 4GB home-rw persistence file, (just rename a blank casper-rw file).

If you delete the Lubuntu partition, I think grub will still work or you can reinstall the Windows bootloader.

---

### Post by AbleTassie on 2018-01-22
Thanks Cameron,

My old PC recognizes  a live boot USB with persistence made by the method below that you, Cameron, suggested in another post on this forum; see below. But my new PC cannot recognize  this same live boot with persistence made by the method.
Yet I am presently using a live boot off a usb (without persistence) on my new PC that was made simply with StartUpDiskCreator. 

Can you or anybody else tell me why this is so?

Thank you,

A.
[B]
Method of making live boot usb with persistence that works on old PC but not new PC:[/B]
[https://ubuntuforums.org/showthread.php?t=1958073&page=71&p=13670206#post13670206](https://ubuntuforums.org/showthread.php?t=1958073&page=71&p=13670206#post13670206)
July 29th, 2017 #20
C.S.Cameron
[https://ubuntuforums.org/showthread.php?t=1958073&page=71&p=13670206#post13670206](https://ubuntuforums.org/showthread.php?t=1958073&page=71&p=13670206#post13670206)
Re: Creating a live boot USB pendrive with persistence for secure use of public WiFi

Following is step by step for installing 16.04 on a 16GB flash drive on an
Intel machine. Start with NTFS format if you want a NTFS Windows
partition, The Windows partition must be the first partition.
Turn off and unplug the computer. (See note at bottom)
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install third-party
software.
Continue.
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table".
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "+".
Make "Size:" about 1000 MB.
Select "Primary".
Location for the new partition = "Beginning of this space".
"Use as:" = "FAT32 file system". (or leave as NTFS).
And Mount point = "/windows".
Select "OK"Click "free space" and then "+".
Select "Size:" = 5000 to 7000 megabytes, "Primary", "Beginning of this
space", Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "+".
Select "Size:" = 1000 to 4000 MB, "Primary", Beginning, Ext2, and
Mount point = "/home" then OK.
(Optional swap space, allows hibernation)
Click "free space" and then "+".
Select "Size:" = remaining space, (1000 to 2000 megabytes, or same size
as RAM), "Primary", "Beginning of this space" and "Use as" = "swap
area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive.
Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, computer name, username, password and select if you
want to log in automatically or require a password.
Requiring a password to log in and selecting "Encrypt my home folder"
are good options if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Note:
You may omit disabling the hard drive if, when partitioning you choose
to install grub to the root of the usb drive you are installing Ubuntu to, (ie
sdb not sdb1). Be cautious, many people have overwritten the HDDMBR.
You can revise grub later, if you wish.
Last edited by C.S.Cameron; July 29th, 2017 at 04:38 PM.

---

### Post by oldfred on 2018-01-22
Acer have an unique requirement of setting "trust" in UEFI. 
Also make sure you have newest UEFI from Acer, some older threads mention downgrading UEFI, but newer ones say newest UEFI works.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

        Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by C.S.Cameron on 2018-01-22
Following is a reprint of a USB Full install method that seems to work in BIOS and UEFI:

Mkusb makes a great base for many bootable pendrive projects, from grub2 bootable Puppy Linux to multiboot Persistent systems to multiboot Full systems and mixed/hybred Persistent/Full systems.

I used the following method to make a BIOS/UEFI Full install:

Use mkusb to make a Live system on a USB (2GB or larger).
Use mkusb to make a Persistent system on a USB 16GB or larger, using default settings with ~12GB persistence.
Remove HDD before proceeding, (optional but recommended).
Insert both USB drives.
Boot Installer drive, select Install.
Select Something else.
Select sdb5, (the target drive), and click Change.
Select Use as: ext4, Format, Mount point /.
Don't touch any other partitions.
Select sdb5 for boot loader installation.
Complete installation.
Cut grub.cfg from sdb5/boot/grub and paste to sdb3/boot/grub, overwriting the existing grub.cfg file.
Delete sdb4, the ISO9660 partition and expand sdb5 into the recovered space.
Boot the target drive and run sudo update grub, (optional).

---

### Post by AbleTassie on 2018-01-26
[SIZE=2]Thanks Cameron and oldFred,

I will look into your recent suggestions.

A.[/SIZE]

---

### Post by AbleTassie on 2018-01-31
[SIZE=2]UPDATE: To repeat: [FONT=&amp]I have a new Acer Aspire E5-575 laptop. It has Windows 10 installed on the HDD. And I want to dual boot Lubuntu.

 I was a bad boy on two counts: I did not read or follow the suggestions here closely and so I did not resize the Windows partition using Windows; **1)** I used Lubuntu live on the HDD install for resizing the Windows partition. **2)** I also did not make a backup image of the Windows 10 OS. But it is newly installed, so I kind of had the impression it can be easily downloaded anew if necessary -- maybe I'm wrong about this though. 

I installed Lubuntu 16.04.2 LTS [/FONT][/SIZE]on the HDD [SIZE=2][FONT=&amp]using an iso image from July 2017 (I had previously checked the MD5SUM and SHA256SUM and there was another signature I checked and these were all OK before.) I used a live boot usb made with StartUPDiskCreator. The HDD is a new SSD. During the install I had an internet connection so it would update to the latest Lubuntu LTS. 
(As I said in a previous post, I had to change the BIOS settings to allow the PC to see the Lubuntu live boot on a USB thumbdrive.)[/FONT]

[FONT=&amp]But I cannot figure out how to boot into the installed Lubuntu. If I push F12 on boot up (with no thumbdrive Lubuntu live on it in a USB port) I get only one choice, to select Windows Boot Manager and boot into Windows 10. If I do not hit F12 on startup, it just automatically boots into Windows 10. [/FONT]

[FONT=&amp]On the other hand, if I have Lubuntu live on a thumbdrive in a USB, I can live boot into Lubuntu and I can see the installed Windows and Lubuntu partitions on the hard drive. And the sizes of the partiton are what I chose (about 300 GB Lubuntu, 200 GB Windows 10). But I cannot boot into the Lubuntu OS on the hard drive.

I have been messing around with Windows 10 and it seems to work, in fact I am writing this post with it right now, so I guess I did not damage Windows 10  by resizing the Windows partition with the Lubunut live boot. In addition, after the Lubuntu install I booted into Windows and Windows repaired the C drive. So I guess I'm OK. I will, however, make an image of the Windows 10 now and any further resizing of the Windows 10 partition, I will use Windows, as suggested here in this thread in a previous post by Yancek.

I contacted Acer Support and they were of little or no help. They gave me a third party help toll free number who told me I could dual boot, but just said to use Google or Youtube to find instructions. Somebody on a forum suggested loading a trusted efi file into the BIOS and if that cannot be done, disabling secure boot.

QUESTION: Does anybody have any other suggestions at this point? If not, I will just try to plow through the links sent to me here before and look at others on this forum to get a feel for the problem.

Thanks,

A. 

**BTW:** I did the install of Lubuntu using the "Install Alongside  Windows" option, rather than using "Something Else" and specifying mount  points and swap partitions, etc. Maybe that explains why I do not get  an option to boot into the Lubuntu that is now on the hard drive.
[/FONT][/SIZE]

---

### Post by oldfred on 2018-01-31
See post #15. 
Acer have unique requirements if UEFI install.

---

### Post by HermanAB on 2018-02-01
Howdy,

I prefer to install Windows as a virtual machine.  That way, I can run Windows in a window on Linux, without having to reboot.  It also avoids getting a corrupted file system when Windows suspends (instead of shut down) and I need to access the NTFS disk from Linux.  I usually install it on Oracle's Virtualbox, but there are multiple virtualizers that all work fine (KVM, Virtualbox, VMWare...).

---

### Post by AbleTassie on 2018-02-01
> **oldfred said:**
> See post #15. 
Acer have unique requirements if UEFI install.

Thanks oldfred,

As I said, I will have to plow through the links sent previously, as in your post #15. I am also educating myself about Secure Boot, trust and UEFI: 
[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot)  and 
[URL="https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot_2"]https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot_2

[/URL]**BTW:** I did the install of Lubuntu using the "Install Alongside Windows" option, rather than using "Something Else" and specifying mount points and swap partitions, etc. Maybe that explains why I do not get an option to boot into the Lubuntu that is now on the hard drive.

 Is there any danger I could "brick" the PC, even if I am conservative in how I approach this?

A.

---

### Post by AbleTassie on 2018-02-01
> **HermanAB said:**
> Howdy,

I prefer to install Windows as a virtual machine.  That way, I can run Windows in a window on Linux, without having to reboot.  It also avoids getting a corrupted file system when Windows suspends (instead of shut down) and I need to access the NTFS disk from Linux.  I usually install it on Oracle's Virtualbox, but there are multiple virtualizers that all work fine (KVM, Virtualbox, VMWare...).

Howdy Herman,

I also am presently virtualizing Windows XP using Virtualbox and Lubuntu on my old machine. But I sometimes have run into problems. For example, I could never get the local public library's Overdrive software to allow downloading audiobooks through the virtualized Windows. All I could do was use an even older PC with dual booted Windows on it that allowed the Overdrive software to work in downloading. Otherwise I hardly expect to use Windows, although I am thinking that there will be other rare times when I just can't get Linux software to do the job. 

Maybe I should make the Windows 10 partition even smaller than 200GB. What do you think?

A.

---

### Post by oldfred on 2018-02-01
If you understand partitions or want a separate /home, it is better to use Something Else.
Most simple installs work with the automatic install option, but you have no control over sizes of partitions.
And If Windows fast start up is on, Linux NTFS tools do not see the Windows partitions and may overwrite them.
Always best to use Windows to shrink the NTFS partition and reboot immediately, so it can run chkdsk which it requires after any resize.

---

### Post by AbleTassie on 2018-02-01
> **oldfred said:**
> If you understand partitions or want a separate /home, it is better to use Something Else.
Most simple installs work with the automatic install option, but you have no control over sizes of partitions.
And If Windows fast start up is on, Linux NTFS tools do not see the Windows partitions and may overwrite them.
Always best to use Windows to shrink the NTFS partition and reboot immediately, so it can run chkdsk which it requires after any resize.

Thanks Fred,

I have made full Lubuntu usb bootable with persistenceinstalls using the something else option and specifying the size of partitions in the past. And I am pretty tech savvy, so I can learn. I am wondering if it might be best at this point to try deleting the Lubuntu partition (that I cannot boot into), then shrinking the Windows partition even further (I think 20GB is the minimum for Windows 10), down to 100GB say, using windows for the resize, make a Windows image for backup and then try installing Lubuntu using the something else option and specifying the size of the partitions and mount points, etc.

What do you and others think?

A friend suggested using Wubi, see [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) . Is using Wubi a good idea?

Thanks again,

A.

---

### Post by oldfred on 2018-02-01
Last supported version of wubi was 12.04, now obsolete.
Wubi was only intended for temporary use. It does not work with new UEFI/gpt partitioned drives, although some third party folks have made it work.

 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)
[https://bugs.launchpad.net/wubi/+bug/1478239](https://bugs.launchpad.net/wubi/+bug/1478239)

---

### Post by AbleTassie on 2018-02-02
Thank Fred,

Do you or others have any suggestions as to whether I should: **1)** just try to get my PC to boot into the current installed Lubuntu on the HDD that was installed using the "along side Windows" option (by trying to reset the UEFI or BIOS) _**vs**_ **2)** delete the currently installed Lubuntu and then reinstall Lubuntu using the "something else" option,  selecting partition sizes and mount points, etc in the hope that this new Lubuntu will bootable?

The presently installed Lubuntu is not available or visible as a boot option during start-up. 

Thanks,

A.

P.S. Somebody has suggested this link [https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027](https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027) as having a protocol for solving the problem. It looks pretty good.

---

### Post by oldfred on 2018-02-02
Since Acer, did you set UEFI password and enable "trust" as posted above?
Multiple users have posted details, but some explain what they did better than others.

---

### Post by AbleTassie on 2018-02-03
OK thanks Fred. I will take it from here and report back.

Thanks again,

A.

---

