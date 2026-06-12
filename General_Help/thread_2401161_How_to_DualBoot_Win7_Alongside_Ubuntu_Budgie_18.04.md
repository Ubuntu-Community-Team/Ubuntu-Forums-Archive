---
title: "How to DualBoot Win7 Alongside Ubuntu Budgie 18.04 with an encrypted HDD and BIOS"
date: 2018-09-14
forum: General Help
---

### Post by lonelybirb47 on 2018-09-14
Hi!
I have few problems i need help with. 
First Id like to install dualboot for gaming purpose on my machine. Sounds easy right? Well not for newb like me. Installing ubuntu on win7 machine was easy , but trying the other way made me desperate. I already did the USB bootable of win7. Yet it doesnt load.

Truth is there were many strange things about my ubuntu installation. From application (Browsers to be specific.) ignoring keyboard input, to slowing down of pc, to freezing (Which i managed to fix somewhat after literally too many hard resets.) to not orderly working BIOS from which Im unable to boot win7. (Could be cause of encrypted HDD?) 
Id like to keep this installation of ubuntu cause of all the stuff i already get on it (Trying python, notepad, movies.. Ve been using it for a month or two.)
Any help? 

Thanks.

---

### Post by lonelybirb47 on 2018-09-14
Eh got a little lost... I need to install win 7 on machine, tried all the way through ubuntu but didnt work any of it. Any help is apprecieted.

---

### Post by yancek on 2018-09-14
> I need to install win 7 on machine, tried all the way through ubuntu but didnt work any of it. Any help is apprecieted. 		

I don't understand the above.  You can't install windows inside Ubuntu unless you are using something like VirtualBox.  If you have a bootable, tested usb with windows 7 on it, you should be able to start that and hopefully, it will have a Custom install option to select a partition on which to install windows.  Have you shrunk your Ubuntu partitions and left either unallocated space on which to install windows or created an ntfs partition for windows?  

How did you create the bootable usb of windows?  What software did you use?  Are you able to test it on another computer to see if it boots?

---

### Post by lonelybirb47 on 2018-09-14
I get rid of VirtualBox after VM win7 which worked without problem excouding drag and drop files through host and guest [win7]. 

Its bootable on other pc and ts installed through ruufus. On this machine its cursed or idk. some blackmagicnickery.However its not selectable in BIOS which is randomly switching with grub.[One time BIOS get started next restart grub boots, which is useless to me.] 
I tried the partitioning but started and am without partitioned HDD. [Is it even possible to parttition encrypted disk?]

---

### Post by oldfred on 2018-09-14
If you have use the encrypted install, that is LVM which is not standard partitioning but logical volumes. You have one large partition with all your logical volumes inside it.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) 
    
Windows will not install to Linux LVM.

If system is less than 5 years old or since Windows 8 released it is UEFI. Did you install Ubuntu in UEFI boot mode or 35 year old BIOS/MBR boot mode?
Windows 7 default DVD is BIOS only. But it can be copied to a flash drive and some files renamed, moved to make it UEFI bootable.

Why would you install Windows if you want full drive encryption. Seems like opposites.
But encryption only protects you when system is fully shutdown. Once you start system to use it, files are un-encrypted.

---

### Post by lonelybirb47 on 2018-09-14
[SIZE=1][I]LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.p...45#post9917145]("http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145")
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[URL="https://wiki.archlinux.org/index.php/LVM"]https://wiki.archlinux.org/index.php/LVM

[SIZE=3][/SIZE]
[/URL] [/I][/SIZE]Thanks for list, checking it out. The resizing part at LVM helped understand what I could do with partioning. 

[I]If you have use the encrypted install, that is LVM which is not standard  partitioning but logical volumes. You have one large partition with all  your logical volumes inside it.     

[/I]If i understand this right I got virtual disk thanks to encryption? Like extra layered for protection and easier management? 

*Windows will not install to Linux LVM.*

So theres no way around that, huh? Id need to reinstall whole machine? 

[I]If system is less than 5 years old or since Windows 8 released it is  UEFI. Did you install Ubuntu in UEFI boot mode or 35 year old BIOS/MBR  boot mode?
Windows 7 default DVD is BIOS only. But it can be copied to a flash  drive and some files renamed, moved to make it UEFI bootable.[/I]

This means ubuntu budgie would be UEFI since its 18.04. However the ruufus installed the win7 in old BIOS/MBR boot mode. Could this be a problem? 
Also making it UEFI bootable i suppose is relateble easy task since you mention it? 

[I]
Why would you install Windows if you want full drive encryption. Seems like opposites.
But encryption only protects you when system is fully shutdown. Once you start system to use it, files are un-encrypted.[/I]

Im forced to encryption for a few reasons. 
But id like to unwind while doing a few things i like apart from studying and or watching movies/listening to music/trying to learn progranmming [which is suck at hah]. 
Once un-encrypted they encript again at beign system shutdown? 



Sorry for newb Qs and hyper written Qs my attention gots affected last few days.

---

### Post by oldfred on 2018-09-14
Virtual disk is different than logical volumes. I have not used either so do not know details.

Ubuntu can be installed in UEFI or BIOS boot mode.

Both Windows & Ubuntu install in the boot mode you use for installer. And that is selected from UEFI boot menu. But Windows 7 default installer is BIOS only so UEFI will only offer the BIOS boot mode. You have to rename boot files as standard .efi boot files for UEFI to see UEFI boot option. 

Ubuntu has both BIOS & UEFI boot configured for UEFI to see when booting flash drive. You may have to turn on/off UEFI settings and USB boot settings to allow UEFI boot or BIOS boot.

If you have multiple drives often better to keep Windows on one & Ubuntu on another. But many now have one SSD and want both on same drive which works, but both need to be in same boot mode.

---

