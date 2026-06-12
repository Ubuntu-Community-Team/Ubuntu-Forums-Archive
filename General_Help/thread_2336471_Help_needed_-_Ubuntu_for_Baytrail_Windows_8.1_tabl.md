---
title: "Help needed - Ubuntu for Baytrail Windows 8.1 tablet?"
date: 2016-09-08
forum: General Help
---

### Post by Jan_Johansson on 2016-09-08
Hi, as the owner of an ODYS WinTab 8 with the same specs below, I like to know if its possible to install Ubuntu to an Windows 8.1 with Bing tablet.

The current windows 8.1 with Bing, is not good on such a small screen  and the way ODYS set it up there are only about 3GB free space out of  the total of 16GB, because of a 5.12GB recovery partition - So if we could get Ubuntu on it instead, and by that  I mean completely erase Windows then it would be wonderful.

Anyone have a suggestion?

HW:

[IMG]http://umpcportal.com/gallery/d/65383-3/odys_wintab_8.jpg[/IMG]

The Odys WinTab 8 is an 8" Windows 8.1  Tablet powered by Intels Bay   Trail-T platform with an Intel Atom Z3735E  quadcore processor. Built in   is a microSDHC slot for expansion of  storage of up to 32GB. 1GB of   RAM. In terms of ports there is only 1 microUSB  port which is host(OTG)   capable and a 3.5mm headphone jack.

[TABLE="class: cms_table_spectable"]
[TR]
[TH="colspan: 2"][/TH]
[/TR]
[TR]
[TD]Manufacturer (Click for list)[/TD]
[TD][Odys]("http://umpcportal.com/database/Odys")[/TD]
[/TR]
[TR]
[TD]Model name[/TD]
[TD]Wintab 8[/TD]
[/TR]
[TR]
[TD]CPU type (Click for list)[/TD]
[TD] [Intel Atom Z3735E]("http://www.umpcportal.com/database?action=search&cputype=201")[/TD]
[/TR]
[TR]
[TD]CPU speed[/TD]
[TD]1330 Mhz[/TD]
[/TR]
[TR]
[TD]Graphics[/TD]
[TD]Intel HD (Gen 7 Baytrail)[/TD]
[/TR]
[TR]
[TD]Fanless[/TD]
[TD]YES[/TD]
[/TR]
[TR]
[TD]OS[/TD]
[TD]Microsoft Windows 8.1[/TD]
[/TR]
[TR]
[TD]Display Size[/TD]
[TD]8.0" 1280 X 800[/TD]
[/TR]
[TR]
[TD]Screen Type[/TD]
[TD] LED-Backlit LCD[/TD]
[/TR]
[TR]
[TD]Touchscreen type[/TD]
[TD] Multi-touch[/TD]
[/TR]
[TR]
[TD]RAM[/TD]
[TD]1024 MB[/TD]
[/TR]
[TR]
[TD]SSD[/TD]
[TD]16 GB[/TD]
[/TR]
[TR]
[/TR]
[TR]
[TD]Battery capacity[/TD]
[TD]16 Wh[/TD]
[/TR]
[TR]
[TD]Weight (Minimum operating)[/TD]
[TD]350gm / 0.77 pounds[/TD]
[/TR]
[TR]
[TD]Size[/TD]
[TD]215/9/99.9 mm[/TD]
[/TR]
[TR]
[TD]Size[/TD]
[TD]8.5/0.4/3.9 inches[/TD]
[/TR]
[/TABLE]

  
 Wireless Interfaces:
802.11 b/g/n
BT 4.0
No Wireless WAN (e.g. 3G cellular)


It has UEFI bios and as far as I can tell its 32Bit.

The bios can be accessed by holding some buttons, so you don't have to boot to windows first.

The partition scheme is as follows:

1. 100MB EFI
2. Windows C:  - Windows 8.1 with bing - 9.30GB with 3.20GB free
3. Recovery - 5.15GB used

Seems to be using Wimboot.

Hope some of the many geniuses here can help with this.

With kind regards

JBJ                 


UPDATE: In the bios there is also an option to boot from Dual boot and Legacy boot, so if there is a possibillity for getting linux on this device:)

I contacted ODYS to ask if it were possible to remove the recovery partition, and the reply were that if I did that then then system might crash, and I would have to install a new windows with a another key - that sound to me like it is possible but I will have to install a new OS myself.

I tried booting of USB stick with my multiboot(using OTG cable) that I used to install Peach OSI 14.04 LTS on my laptop, but only ended up in black screen with frozen cursor, no prompt. I tried the same after I cloned my multiboot to Sandisk USB stick with micro USB and this time with it directly connected to the tablet - same thing.

I tried both Dual boot and Legacy with the same result, so Maybe I do need to make an UEFI linux USB stick.

---

### Post by oldfred on 2016-09-08
With only 1GB of RAM, you should not install Ubuntu, but Lubuntu or Xubuntu.
And 32 bit UEFI is not particularly easy to set up. There are no complete distributions with the compiled 32 bit UEFI. But you do not have to compile as older instructions may say, as the compiled version is avaiable. These 32 UEFI systems were made to be only Windows as Linux did not have a 32 bit UEFI, then.

Other Atom systems, may have enough instructions to help. Have not done it myself, so do not know details.

       [http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393](http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393)
Trying to install Ubuntu on an Acer one 10 (S1002)  32 bit
[http://ubuntuforums.org/showthread.php?t=2305272](http://ubuntuforums.org/showthread.php?t=2305272)
Instructions to install Ubuntu 16.04 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
Packard Bell ENME69BMP InsydeH2O  or Gateway LT41P04u
32-bit UEFI Support Proposed For Ubuntu Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE)
Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)
Asus T100 Compile own grub 32 bit
[http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)
 ASUS Transformer Book T100TA that was one of the early Intel Bay Trail convertible laptops/tablets. 
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

---

### Post by Jan_Johansson on 2016-09-09
Hi oldfred, thank you for the answer and suggestions:)

I have updated my post with new info, please read:)

Which Linux version - Ubuntu or otherwise - works best for Tablet?

Ubuntu support touch that's why I were thinking about that one, I used it on a USB on a friends Surface Pro 2 where the internal eMMC card were busted and it worked(not great as the touchscreen needed calibration and no program or setting for that, so sometimes pressing the screen it jumped around - had to be used with mouse and keyboard). now he got a new eMMC card and installed windows instead.

---

### Post by oldfred on 2016-09-09
The other issue with most of these tablets is unique hardware. Some can use parameters to make a feature work, others just do not have a driver. May depend on what features you must have to know if Ubuntu works. And yes do test with live installer. 

Whether BIOS boot or UEFI boot should not matter. I am a bit surpised that it does allow BIOS boot. Most of these systems were UEFI class 3 or no BIOS emulation chip at all.

With only 1GB of RAM you need Lubuntu or Xubuntu. Ubuntu uses Unity which needs a better graphics card or chip and more RAM to work or work well.

My now 10 year old laptop with 1.5GB did run Ubuntu, but with 12.04 and Unity it was so slow as to be unusable. I had to use terminal to install fallback which is/was the old gnome2 style menus and a much more lightweight gui like Lubuntu. With that laptop if I opened more than one larger app or several smaller apps, it would get very slow and turn grey for a bit. I then knew it was using swap & I had overloaded RAM.

---

### Post by Jan_Johansson on 2016-09-10
Currently using my Lenovo thinkpad R500(64bit system, and 4GB ram) with  Peach OSI 32bit (Xubuntu) 14.04 LTS I tried to follow some of the guides  and tried it out on this laptop, just see if it would boot - it didn't  boot, just ended up with a blank(black) screen with a frozen cursor and  there it stopped - but then again this laptop do NOT have UEFI, could  that be the issue?

I have used 16.04.1 64bit versions of the following .iso Ubuntu, Lubuntu, Xubuntu and Peach OSI BareBones.

On my Peach I have the following programs installed: mkusb, Startup disk creator 0.2.56.3ubuntu0.1, yumi, Multisystem, gdisk.

Could  you give me a guide on how to make a bootable LIVEusb with UEFI support  and persistence, for the above linux versions, so we can rule out HW  failure or typos? Preferebly the one you use yourself. And if possible  multiboot.

Thank you in advance:)

JBJ

---

### Post by oldfred on 2016-09-10
I just manually install grub (either UEFI or BIOS version) and copy ISO to flash drive. Then add boot stanza to loop mount.
But now flash drives are larger & I often just do a full install and then add extra ISO using install's grub.

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

Recent versions have needed these:

 # Required as /isodevice usually mounts to a partition and installer does not correctly unmount
sudo umount -lrf /isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115521](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115521)
Says to use toram boot parameter

---

### Post by Jan_Johansson on 2016-09-13
I'm sorry to say that this tablet might have a HW failure somewhere, because I have tried many Linux distro now including Remix OS 3.0 and all of them boot to grub where you can choose an option and then continue booting and stops with a black screen - then go no further.

I'm putting this on the shelf until someone actually have succeeded in this endavour:)

I suspect that either Intel or AXDIA(ODYS manufacturer) has locked this Device somehow so it only can boot Windows 8.1 with bing.

EDIT: I think i figured out why this tablet go no further than to try and start Linux, according to this article:
[http://hackerboards.com/new-intel-bay-trail-t-socs-target-android-tablets/](http://hackerboards.com/new-intel-bay-trail-t-socs-target-android-tablets/)

The Z3735E cpu seem to ave been crippled so that it can only work with 32bit OS. Strange that it boot to grub menu and starts booting process after choosing the "Try before install" menu item.

So it would seem that I need a 32bit linux that supports 32bit UEFI - and Z3735E cpu - meaning this project is on hold until someone make that possible.

EDIT 2: It would seem that it has nothing to do with the CPU only being able to boot 32bit OS - it boots 32bit Sparky linux i686 fine, and i get to boot menu where I can choose Sparky linux and then I see it booting and ends up in black screen again.

It can possibly be another Intel graphic adapter incompabillity, like there(with trusty) have been in the past with other Intel adapters - I don't know enough about this and so far what I have tried is adding these things to grub.cfg and kernel parameter:

nomodeset

VGA=789

video=VGA-1:1280x800e reboot=pci,force

Nothing seem to work.

Anyone got another idea?

I have dropped the idea of installing and just need an USB stick with persistent or with the OS installed to. Or if possible installed to MicroSD card and SING pLOP or similair to start up.

If someone already got got an USB booting on this kind of tablet then I would be greatfull for a link to an Image file of the working USB stick(no more than 16GB, as 32GB might not fit my 32GB stick due to manufacturer difference) so I can test if it will boot on mine.

---

### Post by Jan_Johansson on 2016-09-22
UPDATE: After information from the manufacturer, it would seem that in order to boot from USB on this tablet, your need and powered USB hub, because the USB port on the tablet only have enough power for the initial boot process but not enough for the rest - that is why the boot seem to work and then fails.

Also, this tablet cannot boot from MicroSD card.

I have an All-in-one USB hub and will see if I can find the adapter of 5V 500mAh - But it somewhat defeats the purpose of being mobile, unless you install Linux and then remove the extra equipment - but there, simply put, is not enough free space for that, because of the stupid partition scheme the manufacturer has done.

Unless there are some super lightweight linux distro that support tablet and can fit into 1-3GB space outthere. Or one that can be installed onto MicroSD card and initial booted from ROM and then continued booted from MicroSD. Take in mind that this should be done from within Windows 8.1 With Bing, because within windows all the drivers for USB are loaded  and it has full power - and there are no problem at all reading the USB.

Anyone know of one?

---

### Post by Jan_Johansson on 2016-10-16
The effort on getting linux on this tablet continues here:

[https://linuxiumcomau.blogspot.com/2016/10/running-ubuntu-on-intel-bay-trail-and.html?showComment=1476614678955#c2971567844614286584](https://linuxiumcomau.blogspot.com/2016/10/running-ubuntu-on-intel-bay-trail-and.html?showComment=1476614678955#c2971567844614286584)

And here:

[http://www.murga-linux.com/puppy/viewtopic.php?t=108295](http://www.murga-linux.com/puppy/viewtopic.php?t=108295)


Look for my post by JBJ and Insomniacno1

---

