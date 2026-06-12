---
title: "Remove (not repair) grub"
date: 2014-11-30
forum: General Help
---

### Post by DonDodge on 2014-11-30
I have a hard drive (1 TB WD Caviar Black) that has grub in an unallocated space. There are 4 partitions on the drive and all are formatted to NTFS plus the grub in the 2.5 MB unallocated space. 

Whenever I install this drive in a computer, the grub wants to take over and try to boot the computer by going to a "grub rescue" prompt. It also messes with my ability to enter the BIOS or use other means to choose my boot drive. 

There's a whole world of information available about how to repair/restore grub but how in the world do you completely remove the grub from a hard drive that doesn't need it or want it?  Gparted offers no help at all. Nothing it can do with the unallocated space where the grub lives. Ideally I would like to remove the grub without goofing with partitions on the drive.

Is there a Grub Rescue command that will nuke the grub and delete it from the drive?
Can I do this from a distro Live CD?

---

### Post by ajgreeny on 2014-11-30
What OS is now on the machine?  Does it have Windows 7 or 8?
If it does, you need to restore the windows bootloader from your DVD of that, or from the repair disk that you should have made when you first ran Windows.

You did make that repair disk didn't you?

---

### Post by DonDodge on 2014-11-30
I have Windows 7 on the main drive and the bootloader/MBR/Bootrec of that disk is just fine.

The problem is the grub on a completely different disk that has no OS on it whatsoever. I just need to get rid of the grub on that disk.

---

### Post by papibe on 2014-11-30
Hi DonDodge.

Check the command 'install-mbr' from the package mbr. [Here]("http://askubuntu.com/questions/131168/how-do-i-uninstall-grub") is an example (scroll down a few answers).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by DonDodge on 2014-11-30
Thanks papibe. I'll disconnect my main drive, boot to a live cd and see what I can do with some of this.

It would be a lot easier if the ignorant UEFI bios in this machine would simply let me set a pre-determined boot order and be done with it. This is like herding cats.

If all else fails maybe I can use the Windoze install disk to get a prompt and throw some bootrec commands at the grub and get rid of it that way.

---

### Post by grahammechanical on 2014-11-30
I do not know if this will work with a Ubuntu live session and If I had a second hard disk with other OS on it I would disconnect it first before trying it.

> [COLOR=#333333][FONT=Ubuntu]Remove GRUB 2[/FONT][/COLOR]
[LIST]
[*=left][FONT=inherit]sudo apt-get purge grub-pc[/FONT]
[*=left][FONT=inherit][[IMG]https://help.ubuntu.com/moin_static192/light/img/attachimg[/IMG]]("https://help.ubuntu.com/community/Grub2/Uninstalling?action=AttachFile&do=upload_form&ticket=00547bbf69.7f1b4822fb807dff49ca9c95f5add508b87059e8&target=important.png") The system will be unbootable until another bootloader is installed.[/FONT]
[/LIST]


I am not sure if that command will remove the Grub from the MBR or just the rest of Grub from a Ubuntu installation.[URL="https://help.ubuntu.com/community/Grub2/Uninstalling"]

https://help.ubuntu.com/community/Grub2/Uninstalling[/URL]

I take it you do not want any boot loader on the 1TB disk.

EDIT: a quick scan through the Grub manual did not yield any information about un-installing Grub from the MBR but the file that you need to get rid of is boot.img. That is what gets put into the MBR when Grub is installed.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It will purge Grub and restore a compatible Windows MBR.

Regards.

---

### Post by DonDodge on 2014-11-30
Best I can tell there are no files on this disk because I formatted all the partitions with Gparted. Also, best I can tell is the grub lives in a small part of the drive called unallocated space that Gparted can't do anything with. The only option Gparted gives me for this area is "New" but that goes nowhere since there are already 4 partitions on the drive.

I don't want this drive to be bootable. Alll I need it for is storing data and maybe sometime later installing a Linux distro in the first 40 GB partition. Now all I want to do is get rid of the grub on the drive.

---

### Post by oldfred on 2014-11-30
Post link to summary report from this. It will show where grub is at.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

We rarely erase grub from an MBR. It that drive is not used fro booting it does not matter what is in drive. Just do not have it in BIOS boot order.  Or if new system is installed then MBR is over written.

If UEFI then that is a lot different. Summary report will tell us details.

---

### Post by ajgreeny on 2014-12-01
I am not totally certain of this, but I think I recall reading that making a new partition table with the Device menu of gparted will also remove grub from the MBR.

You **must** backup any files you have on that disk first as everything will be wiped out (including grub, I hope) and after making the new partition table you will need to make a new partition, or partitions.

---

### Post by DonDodge on 2014-12-01
Okay, here's what I had to do to remove the Grub from this drive. I got it finished last night.

I had high hopes the "sudo apt-get purge grub-pc" command would work. The dialog presented in the transaction every time I ran it indicated it was working and deleting something like 614 kb of data but that did not kill the Grub or remove the Grub Rescue prompt

Gparted or Live CD offered no help in removing the grub which was 2.0 Ubuntu version something or another.  No format or partition manipulation would touch the grub. The Live CD did allow me to move all my data off the drive with the problem so I pounded that sucker half to death trying to kill the grub both from Linux and Windoze. I deleted and rebuilt partitions every way possible but the grub persisted

I had already changed Secure Boot in this godforsaken UEFI bios from Windows to Other OS. I did that a few days ago when I learned the third consecutive boot attempt with an Acronis CD or other non-windoze media would lock me out of the bios requiring me to manually clear the RTC RAM.

I changed the bios Compatibility Support Module to Legacy OpRom only to (hopefully) kill the UEFI in this thing. Computer still boots to the grubbed drive.

Note: there is no way to set a pre-determined boot order in this stinkin' bios. It simply does whatever it wants to and if you screw with it too much the punk locks you out.

Disconnect all other hard drives from the computer and run the WIn 7 install until I could get to the command prompt. From there I ran
bootrec /fixmbr
and hit a dead end

Reboot the same way and get the command prompt to run

bootrec/fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /RebuildBcd

This finally killed the Grub and gave me a simple and highly appreciated bootloader error.

From there I reconnected the other drives but the computer insisted on booting to the drive with no bootloader.

I rebuilt the the C: drive boot section with the same procedure as above.
bootrec/fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /RebuildBcd

This finished it and the computer now boots and functions normally and as it should.

I'm not too fluent on new computers since I only change parts as needed. The computer I just built replaced an 8 year old CPU and memory and a 4 year old motherboard. This EUFI garbage is a whole new world.

I think the UEFI combined with the Grub made for some of the worst computer problems I've had in 30 years. I didn't lose any data and didn't have to reinstall anything in this mess that went on for a few days but I've never come closer to losing an entire computer and all my data in my life. Good thing I have multiple computers, a large USB hard drive and Acronis on another computer or I would have lost everything. Thank goodness for Acronis and a Live CD. When my main Windoze install got shelled and I started getting GPT/MBR errors, I dumped an image onto another partition of my main drive and turned that into the C:

Here's the basics of this system That I put into service a month ago.
ASUS M5A97 LE R2.0 970 AM3+ R
AMI bios 1/6/2014 version 2301
AMD FX-6300 Vishera 6-Core 3.5GHz
AMD 6-CORE FX-6300 3.5G 8M R
2X 8GB KINGSTON HyperX Fury Black Series 240-Pin DDR3 1600 (PC3 12800) HX316C10FB/8 R
Nvidia GeForce 7300 LE Driver Version 307.83
3X WD Caviar Black hard drives
Windows 7 x64 Home Premium Version 6.1 (Build 7601 SP1)
And the ill-fated install of Linux Mint Mate 17

I also know where I screwed up in this deal. I did a quick test install ot Linux Mint Wednesday night and didn't pay attention to where the Grub was installed. I allowed it to go onto the non Windows drive containing the Linux install. It was all downhill from there.

Comments, advice and reprimands are welcome.

---

### Post by oldfred on 2014-12-01
D It sounds like you converted your new UEFI system to the 35 year old BIOS system. That will work as they still offer BIOS mode with new UEFI systems.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

UEFI requires the new gpt partitioning, but Ubuntu can boot in BIOS mode from gpt partitioned drives. Windows only boots in UEFI mode from gpt drives. All pre-installed Windows 8 systems use UEFI and all Mac since they converted to Intel chips have used an older version of UEFI.

But UEFI is a lot different and usually requires some (many) settings in UEFI to configure it correctly. And how you boot install media UEFI or BIOS is how it installs. 
UEFI and BIOS are not compatible as they load drivers differently, so you cannot dual boot systems with one install in UEFI and anther in BIOS unless you totally reboot and choose other from UEFI/BIOS menu. Sometime one time boot key works.

I just installed a new system with Asus A97-AR for Intel chips. I had to change a lot of settings to get it to boot. One was the Windows or 'other' operating system which I believe is what they are calling secure boot in UEFI. And then all the UEFI settings were buried under the CSM mode settings.

Do not know if your AMD chip has video, but the Intel internal video is about equivalent to my older 9600GT, so your old nVidia card may not work well with new system.

---

### Post by DonDodge on 2014-12-01
The computer is running off what is fundamentally the initial DVD install of Wiin 7 I had to do for this new computer. That was done long before any changes were made to the bios so the installer did whatever it wanted to do upon first boot of the computer with the bios in out of the box default mode.  I assume that must have been UEFI.

The only thing that's really different now is I had to change the bios to make the computer work properly after screwing things up with the Linux install to a different drive.  I never had to touch a thing on the Disk 0 or Disk 1. Whatever Win 7 did to it during the initial install should still be in effect unless it only worked it's GPT magic on the first partition of Disk 0 where I installed it. Now the original Windows is running on the third partition of Disk 0.

The only thing I know to do differently is remove the 1 TB drive that was apparently trashed by the grub and leave it out of the system. Seems like a waste.

I'll move the bios back to Secure Boot Windows/UEFI mode and see what it says now that the Grub is history. But should I really care about UEFI unless I want to use drives larger than 2 TB? I do have a 2 TB USB 3.0 that lives in the safe.

Oh, I guess there are no problems with the old video card. This motherboard has no on-board video. Windows did what it wanted to with it and installed the drivers for it. I suppose it downloaded all the nvidia control panels through Windows Update. I never did a thing for installing the card except plug it in and connect the monitor to the DVI port.

---

### Post by oldfred on 2014-12-01
Windows 7 normally defaults to BIOS with MBR partitioning.
I think you have to convert DVD to flash drive and make a couple of minor changes to make it be an UEFI installer. Windows 8 can be installed in either BIOS or UEFI boot mode.

It then sounds like with Windows in BIOS mode on one drive, you then changed boot to UEFI and installed Ubuntu in UEFI boot mode on the other drive. And that is very confusing and can be difficult to manage.
Boot-Repair allows you to convert Ubuntu UEFI to BIOS or BIOS to UEFI if on gpt partitioned drive.
Do not think you can convert Windows without full reinstall which is not worth it now.

---

### Post by DonDodge on 2014-12-01
Well, the good news is I changed the bios Secure Boot back to Windows UEFI mode and the Compatibility Support Module back to UEFI and Legacy OpRom. The computer boots and works just fine with no attempts to go to the other hard drive on boot. One thing it doesn't seem to like is a UEFI Atapi boot to an Acronis boot and rescue disk but I can live with that by controlling the boot to make it go with a plain Atapi boot.

I looked around a bit more and learned Wiindoze can't do the GPT thing without giving it a clean, unpartitioned drive. Really, I could give a hoot about all this next generation malarkey. I just want my computer to work so I can run my business.

The only Win 8 computer we have is a laptop with pre-installed 64 bit OS. I suppose that's GPT and UEFI but I don't know. I set it up, upgraded it to 8.1, installed the stuff it needed and the stuff it needed to look more like a real computer and gave the damned thing to my wife.

Edit: I just burned an Acronis 2015 boot disk and that does just fine with the UEFI boot.

---

