---
title: "How To BOOT from an ISO image within my Dowloads folder?"
date: 2015-12-10
forum: General Help
---

### Post by Davekyn on 2015-12-10
**Main Objective** = To install a Linux Distro onto an External HDD.

**Current Dilemma** = Launching Software Installation/Iso Image from within my Desktop.  I do not want to run from USB or CD as I am installing to an external HDD. 
 I can mount the Image - [IMG]http://i181.photobucket.com/albums/x30/davekyn/Selection_013_zpsoaaphhvf.png[/IMG]

But having issues locating any kind of Setup .exe within the mounted folder.  Of course I am out of my depth given I am completely new to Linux and unfamiliar with the file types and yadda yadda.
____________________________

Would someone please be kind enough to [COLOR="#FF0000"]simply explain how I can "run" the application from this iso image "from within my downloads folder"[/COLOR] so that I can begin installing onto my external drive.

**Additionally**, once installed on the external drive, [COLOR="#FF0000"]how does one boot into the newly installed OS on the external HDD?[/COLOR]
_________________________________________________________
[SIZE=1][I]
**Disclaimer** - [COLOR="#696969"]Yes the question has been asked before and my terms are all wrong. Thanks for bringing that to everyone’s attention. Now if "someone else" would be kind enough to actually help. Thank you.[/COLOR][/I][/SIZE]

---

### Post by sammiev on 2015-12-10
Hi and Welcome,

If you mean running an ISO from a Windows OS, then I would suggest installing a VM ( virtual box ) and installing the Linux ISO into the VM.

If you want to run a ISO from a Linux OS you can still use a VM or [read this]("http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/").

---

### Post by oldfred on 2015-12-10
You have to boot installer, you cannot run it from inside another operating system.
Is system UEFI or BIOS?

You can directly boot an ISO, using grub2 boot loader, but not the Windows boot loader. But that is a bit more advanced as you have to understand some of grub, paths and boot stanza.
  How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images
[http://ubuntuforums.org/showthread.php?t=2276498](http://ubuntuforums.org/showthread.php?t=2276498)
      
 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

If you just have Windows on internal drive it is just about impossible to do. Better and easier to use flash drive.

---

### Post by Davekyn on 2015-12-11
Awsome.  Thx for the speedy replies.  I'm out atm, so will have to catch up later.  I'll atempt to further explain then.  
I left the house with web pages on creating a usb start up disc.  
Best leave this post till I get back.
Thx for the support ... catch up soon enough. 
Great links. Cheers.

---

### Post by Davekyn on 2015-12-11
I managed to make a bootable install USB stick, however ended up with a failed instillation due to Grub issues.
Not  really in the mood to go into detail at this time, except to say I need  more time to assimilate and comprehend all the workings within the provided  Links.  It's all still a little over my head.

I  may attempt to install Linux Mint alongside Ubutnu instead.  When I  gain more knowledge as to how linix and the computer works, I may be  then more savy to work things out.

I think I will cop out for now. 

Maybe pick this up again tomorrow, maybe not. 

Thx again for your help.

---

### Post by oldfred on 2015-12-11
Newer UEFI or older BIOS?

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

