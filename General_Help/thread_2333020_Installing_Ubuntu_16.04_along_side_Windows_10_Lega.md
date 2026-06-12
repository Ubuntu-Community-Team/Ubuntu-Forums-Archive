---
title: "Installing Ubuntu 16.04 along side Windows 10 Legacy Bios"
date: 2016-08-06
forum: General Help
---

### Post by swarup on 2016-08-06
I have a Dell Vostro laptop with Windows 10, which is a legacy bios rather than a UEFI. I have downloaded 16.04 and created a bootable USB using Rufus. I've tested the bootable USB on my other laptop which is of type UEFI, and the computer boots to the bootable USB perfectly, into 16.04. I've set up the Dell Vostro boot order to look first for a bootable USB. When I start up the dell with the bootable usb plugged in, I get a black screen with a cursor, and nothing further happens. Please let me know why it is not booting to the usb. Would the same bootable usb work for UEFI and legacy bios? Or does one need to somehow setup the bootable usb differently if it is to be used for a UEFI computer vs one with legacy bios?

---

### Post by grahammechanical on 2016-08-06
Do you get a purple screen with icons of a human and a keyboard? If you do, then press Enter. Select a language (default is English) and at the underlying screen press F6. A small menu will appear. Select nomodeset.

See Changing the CD's default boot options. Section 6 - F6.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards

---

### Post by Mark Phelps on 2016-08-06
Word of CAUTION: Do NOT, repeat NOT, use the "alongside" option of the installer to shrink the Windows filesystem partition to make room for Ubuntu.

In the past, this has often lead to corruption of the Windows filesystem, preventing Windows then from rebooting, making it very hard to fix.

Instead, use the Windows Disk Management tool to shrink any Windows partitions.

Good Luck

---

### Post by swarup on 2016-08-06
@grahammechanical: There is no purple screen, and no icons. It is just a black screen with a single blinking cursor in the upper left corner in which I cannot type anything. And I tried the pressing various function keys at startup, but nothing at all happened.
@Mark Phelps: Thanks for the tip. I had ready various guides before starting, and so yes I've already shrunk the windows partition using the Windows Disk Management tool, prior to trying to install Ubuntu.

Right now as mentioned, I just have a black screen when I boot up the computer with the bootable usb drive plugged in. Any suggestions welcome...

---

### Post by oldfred on 2016-08-06
The Ubuntu USB flash drive installer is both UEFI and BIOS installer. It is just how you boot it is then how it installs. And if only a BIOS system it only boots in BIOS boot mode.

Often black screen is a video issue and boot parameter required. Sometimes different boot paramter(s) needed instead of or in addition to video parameter.

What video card/chip?

Before install you should with BIOS, get two tiny accessiblity icons at bottom of screen. Press any key while they show, then f6.
       After install, at grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by swarup on 2016-08-06
@oldfred:
1. The components of the computer are found in the "System Information" screen. There under multimedia there are five video "codecs", all made by Windows. When I search on "video card" or "video chip", nothing comes up. So perhaps it is just these five codecs. 
2. "Before install you should with BIOS, get two tiny accessiblity icons at bottom of screen." I am not getting this at all. Just a black screen with a blinking cursor. No "accessibility icons" at bottom of screen.

So, what are the different boot paramter(s) which are needed? Or, how can I find out what they should be?

---

### Post by swarup on 2016-08-06
@oldfred: I've just gone to all four of the links you've given and gotten an overview of what they provide. To me it seems like you need to either have Ubuntu installed (in order to open a terminal window to execute the commands they request one to do), or be able to get to a grub screen (in order to type in the commands and changes they suggest for grub). But all I get when I boot with the bootable usb installed, is a black screen-- completely black-- with a blinking cursor that doesn't allow anything to be typed. There is no question of a grub screen or anything like that. So at this point I don't understand how those four links can help me. Or if you see a way that they can, please give me some suggestions or guidance as to how I could execute them without a grub screen or a terminal window.

---

### Post by Geoffrey_Arndt on 2016-08-06
You must intervene . . . **before** the boot sequence finishes on the usb.    Hold down the Right SHIFT key during bootup.   IF that doesn't display the accessibility icons or the bootup grub options screen, try the ESC key while you're booting up.   You likely have either amd/ati or nvidia proprietary graphics (versus Intel integrated graphics), so the installer on certain hardware fails to the BSOD (Black Screen of Despair) . . .

---

### Post by swarup on 2016-08-06
@Geoffrey_Arndt: I just tried your suggestions--
1) Hold down the Right SHIFT key during bootup. 
2) Hold down the  ESC key during bootup. 

Nothing changed with either of the above approaches. It still just gives me a completely black screen with a cursor that won't allow typing in. There is nothing else; no accessibility icons, and no bootup grub options.

---

### Post by oldfred on 2016-08-06
The one link shows the icons at the bottom. You only get that for a few seconds just after BIOS and before it opens more screens.

You only get grub menu after install or if installing with UEFI. So you should not have grub menu until after install.

If not getting anything on screen is it a valid boot disk for your system. My older BIOS systems would not boot a USB flash drive but same flash drive was bootable as another hard disk entry in BIOS boot menu. It took me a long time to realize I was in the wrong mode. My BIOS had many USB boot options none of which worked, only another hard drive was seen.

---

### Post by swarup on 2016-08-06
- There are definitely no icons at bottom of screen, not even for a few seconds.

- You ask is it a valid boot disk for my system. The computer, an upscale business model Dell, is less than 2 years old, probably around 1 year old, and is a 64-bit PC, running Windows 10. On the Ubuntu download site, I only see one option, the "64-bit PC (AMD64) desktop image". Is there a different option I should be considering?

---

### Post by oldfred on 2016-08-06
That should be corret. You want the 64 bit version.

When you boot flash drive you should have two options one UEFI:flash drive and the other just the name/label of flash drive (BIOS). You want the UEFI option and then should get grub menu.

If system was 4 or 5 years old with Windows 7 then it would probably be a BIOS system.

---

### Post by Geoffrey_Arndt on 2016-08-06
Another option . . sometimes easier on certain PC's, is to burn a bootable DVD versus using the flash-stick.

---

### Post by swarup on 2016-08-07
Actually I just bought this computer from a used computer depot, and I think they said it originally had Windows 8 on it, so that may put it perhaps 2 years old? Not certain on the date. It is a BIOS system as I mentioned earlier, not a UEFI. But it is surely 64 bit, and so the flash drive should be working fine with it. I could try the DVD and see if it makes any difference.

---

### Post by oldfred on 2016-08-07
If it was originally Windows 8 then it really is UEFI. But some vendors to avoid confusion (but create more) call it BIOS.
Windows 8 or later is required by Microsoft to be installed with UEFI Secure Boot on. BIOS has no Secure boot mode.

---

### Post by Geoffrey_Arndt on 2016-08-07
IF so, that also means you have to find where the option is, . . . to turn secure boot OFF/Disable, so the usb flash-stick will load.\\

Is there a model number to the Dell Vostro so the technical specs can be looked up?    Providing "detailed" machine specs is always a good place to start.   Obviously, that doesn't matter on most Windows machines as they are pre-designed for Windows, but it does make a difference if trying to retrofit a PC with another OS.    There should be a specific users guide PDF and or Technical Manual PDF that can clear much of these mis-assumptions up.

Interesting sidenote . . . I see the newer Dell Vostro 15 5000 series offers the choice to order "pre-installed" with Ubuntu, instead of just the usual Windows flavors.    Again, "which" Vostro model do you have?

---

### Post by swarup on 2016-08-07
@oldfred: Whatever may be the case, according to the info my Windows 10 is providing me, it is a legacy bios and not a UEFI system. Going into Windows 10 on the laptop, there into "System Information", it clearly lists the Bios type as "Legacy". There if it was UEFI, it would have said "UEFI". See the pictures at the beginning of the tutorial in these two links:

[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside_8.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside_8.html)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

I was pretty sure that the guy at the computer depot told me it had Windows 8 on it and they were putting Windows 10 on it for me. But that is just what I recall him having said. It may be mistaken, because oldfred says "Windows 8 or later is required by Microsoft to be installed with UEFI", and as per the information in my Windows 10, the BIOS is listed as LEGACY, and not as UEFI.

@Geoffrey_Arndt: The computer is a Dell Vostro 1440 14" I3 Laptop Windows 10 4 GB Ram 500 GB HD/

---

### Post by oldfred on 2016-08-07
If you let store re-install system, they may not have installed in UEFI mode. (many do not even know difference).
And Windows when reinstalled in BIOS/MBR over UEFI/gpt does not re-partition drive correctly. 
It leaves the backup gpt partition table. Windows seems to ignore it?

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by swarup on 2016-08-08
It's midnight now my time. Tomorrow I'll call the computer depot and confirm with them whether this is what happened-- i.e.reinstalled in BIOS/MBR over UEFI/gpt. If so, then I will try FixParts and see if that takes care of it. I guess you are saying that once I run FixParts, the bootable ubuntu flashdrive should work...

---

### Post by Geoffrey_Arndt on 2016-08-08
Am pretty sure a bootable DVD will work on this laptop.  The specs say the laptop came with Windows 7 . . . so your age estimation may be off somewhat.

[http://www.cnet.com/products/dell-vostro-1440-14-core-i3-370m-3-gb-ram-320-gb-hdd/specs/](http://www.cnet.com/products/dell-vostro-1440-14-core-i3-370m-3-gb-ram-320-gb-hdd/specs/)

---

### Post by oldfred on 2016-08-08
Windows 8 release date: October 26, 2012. 
But many business stayed with Windows 7 for years after Windows 8 came out.
But some later versions of Windows 7 were installed in UEFI boot mode.
If Intel i3, hardware is almost for sure UEFI, but Windows then can be either UEFI or BIOS.

---

### Post by swarup on 2016-08-08
This Ubuntu installation is seeming somehow ill-fated. Three DVD-R's have been ruined trying to burn the iso. The iso "ubuntu-16.04.1-desktop-amd64" downloaded seamlessly and is 1.5 GB size in my download folder. My DVD burner has always worked perfectly.  Here below is the output of the last attempt. I do not know why there should be a problem, but mid-way through the burn process it keeps giving an error and ejecting the DVD. 97% of the way through the burn, the software says "Fatal error during recording: Input/output error. 

```
Burned media
-----------------------
DVD-R Sequential

Devices
-----------------------
MATSHITA DVD-R   UJ-868 KB19 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.14.13
QT Version:  4.8.6
Kernel:      3.13.0-92-generic

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: engaging DVD-R DAO upon user request...
/dev/sr0: reserving 738920 blocks
/dev/sr0: "Current Write Speed" is 8.2x1352KBps.
   10125312/1513308160 ( 0.7%) @1.8x, remaining 12:22 RBU 100.0% UBU   2.0%
   25853952/1513308160 ( 1.7%) @3.4x, remaining 7:40 RBU 100.0% UBU  87.8%
   41680896/1513308160 ( 2.8%) @3.4x, remaining 6:28 RBU 100.0% UBU  87.8%
   57507840/1513308160 ( 3.8%) @3.4x, remaining 6:19 RBU 100.0% UBU  87.8%
   72548352/1513308160 ( 4.8%) @3.3x, remaining 5:57 RBU 100.0% UBU  87.8%
   88768512/1513308160 ( 5.9%) @3.5x, remaining 5:37 RBU 100.0% UBU  81.6%
  105086976/1513308160 ( 6.9%) @3.5x, remaining 5:35 RBU 100.0% UBU  83.7%
  121536512/1513308160 ( 8.0%) @3.6x, remaining 5:20 RBU 100.0% UBU  83.7%
  137396224/1513308160 ( 9.1%) @3.4x, remaining 5:10 RBU 100.0% UBU  83.7%
  153321472/1513308160 (10.1%) @3.4x, remaining 5:10 RBU 100.0% UBU  79.6%
  170328064/1513308160 (11.3%) @3.7x, remaining 4:59 RBU 100.0% UBU  79.6%
  187269120/1513308160 (12.4%) @3.7x, remaining 4:50 RBU 100.0% UBU  79.6%
  204308480/1513308160 (13.5%) @3.7x, remaining 4:48 RBU 100.0% UBU  79.6%
  220069888/1513308160 (14.5%) @3.4x, remaining 4:42 RBU 100.0% UBU 100.0%
  237371392/1513308160 (15.7%) @3.7x, remaining 4:34 RBU 100.0% UBU 100.0%
  254803968/1513308160 (16.8%) @3.8x, remaining 4:31 RBU 100.0% UBU 100.0%
  271810560/1513308160 (18.0%) @3.7x, remaining 4:24 RBU 100.0% UBU 100.0%
  288587776/1513308160 (19.1%) @3.6x, remaining 4:18 RBU 100.0% UBU 100.0%
  306348032/1513308160 (20.2%) @3.8x, remaining 4:16 RBU 100.0% UBU 100.0%
  324173824/1513308160 (21.4%) @3.9x, remaining 4:09 RBU 100.0% UBU 100.0%
  340557824/1513308160 (22.5%) @3.5x, remaining 4:04 RBU 100.0% UBU 100.0%
  358940672/1513308160 (23.7%) @4.0x, remaining 4:01 RBU 100.0% UBU  89.8%
  377225216/1513308160 (24.9%) @4.0x, remaining 3:54 RBU 100.0% UBU  87.8%
  395640832/1513308160 (26.1%) @4.0x, remaining 3:48 RBU 100.0% UBU  87.8%
  412549120/1513308160 (27.3%) @3.7x, remaining 3:46 RBU 100.0% UBU  83.7%
  431194112/1513308160 (28.5%) @4.0x, remaining 3:40 RBU 100.0% UBU  83.7%
  449937408/1513308160 (29.7%) @4.1x, remaining 3:35 RBU 100.0% UBU  83.7%
  468877312/1513308160 (31.0%) @4.1x, remaining 3:31 RBU 100.0% UBU  83.7%
  486211584/1513308160 (32.1%) @3.8x, remaining 3:27 RBU 100.0% UBU  77.6%
  505380864/1513308160 (33.4%) @4.1x, remaining 3:21 RBU 100.0% UBU  77.6%
  524648448/1513308160 (34.7%) @4.2x, remaining 3:17 RBU 100.0% UBU  77.6%
  542212096/1513308160 (35.8%) @3.8x, remaining 3:13 RBU 100.0% UBU  75.5%
  561971200/1513308160 (37.1%) @4.3x, remaining 3:07 RBU 100.0% UBU 100.0%
  581533696/1513308160 (38.4%) @4.2x, remaining 3:04 RBU 100.0% UBU 100.0%
  601325568/1513308160 (39.7%) @4.3x, remaining 2:58 RBU 100.0% UBU 100.0%
  619610112/1513308160 (40.9%) @4.0x, remaining 2:54 RBU 100.0% UBU 100.0%
  639598592/1513308160 (42.3%) @4.3x, remaining 2:50 RBU 100.0% UBU 100.0%
  659750912/1513308160 (43.6%) @4.4x, remaining 2:45 RBU 100.0% UBU 100.0%
  678330368/1513308160 (44.8%) @4.0x, remaining 2:41 RBU 100.0% UBU  79.6%
  698712064/1513308160 (46.2%) @4.4x, remaining 2:37 RBU 100.0% UBU  79.6%
  719192064/1513308160 (47.5%) @4.4x, remaining 2:32 RBU 100.0% UBU  79.6%
  739803136/1513308160 (48.9%) @4.5x, remaining 2:27 RBU 100.0% UBU  79.6%
  758874112/1513308160 (50.1%) @4.1x, remaining 2:24 RBU 100.0% UBU  77.6%
  779681792/1513308160 (51.5%) @4.5x, remaining 2:19 RBU 100.0% UBU 100.0%
  800686080/1513308160 (52.9%) @4.5x, remaining 2:14 RBU 100.0% UBU 100.0%
  820084736/1513308160 (54.2%) @4.2x, remaining 2:11 RBU 100.0% UBU 100.0%
  841285632/1513308160 (55.6%) @4.6x, remaining 2:06 RBU 100.0% UBU 100.0%
  862257152/1513308160 (57.0%) @4.5x, remaining 2:01 RBU 100.0% UBU 100.0%
  882343936/1513308160 (58.3%) @4.3x, remaining 1:57 RBU 100.0% UBU  75.5%
  903741440/1513308160 (59.7%) @4.6x, remaining 1:53 RBU 100.0% UBU  77.6%
  925630464/1513308160 (61.2%) @4.7x, remaining 1:48 RBU 100.0% UBU  77.6%
  945618944/1513308160 (62.5%) @4.3x, remaining 1:45 RBU 100.0% UBU  77.6%
  967573504/1513308160 (63.9%) @4.8x, remaining 1:40 RBU 100.0% UBU 100.0%
  989626368/1513308160 (65.4%) @4.8x, remaining 1:35 RBU 100.0% UBU 100.0%
 1005420544/1513308160 (66.4%) @3.4x, remaining 1:33 RBU 100.0% UBU  89.8%
 1027440640/1513308160 (67.9%) @4.8x, remaining 1:28 RBU 100.0% UBU  89.8%
 1050116096/1513308160 (69.4%) @4.9x, remaining 1:24 RBU 100.0% UBU  89.8%
 1072660480/1513308160 (70.9%) @4.9x, remaining 1:20 RBU 100.0% UBU  89.8%
 1095073792/1513308160 (72.4%) @4.9x, remaining 1:15 RBU 100.0% UBU  89.8%
 1118109696/1513308160 (73.9%) @5.0x, remaining 1:11 RBU 100.0% UBU  89.8%
 1140817920/1513308160 (75.4%) @4.9x, remaining 1:06 RBU 100.0% UBU  89.8%
 1164050432/1513308160 (76.9%) @5.0x, remaining 1:02 RBU 100.0% UBU  89.8%
 1187217408/1513308160 (78.5%) @5.0x, remaining 0:57 RBU 100.0% UBU  89.8%
 1210515456/1513308160 (80.0%) @5.0x, remaining 0:53 RBU 100.0% UBU  89.8%
 1232273408/1513308160 (81.4%) @4.7x, remaining 0:49 RBU 100.0% UBU 100.0%
 1255800832/1513308160 (83.0%) @5.1x, remaining 0:45 RBU 100.0% UBU 100.0%
 1279459328/1513308160 (84.5%) @5.1x, remaining 0:41 RBU 100.0% UBU 100.0%
 1303216128/1513308160 (86.1%) @5.1x, remaining 0:36 RBU 100.0% UBU 100.0%
 1327104000/1513308160 (87.7%) @5.2x, remaining 0:32 RBU 100.0% UBU 100.0%
 1349484544/1513308160 (89.2%) @4.8x, remaining 0:28 RBU 100.0% UBU  77.6%
 1373405184/1513308160 (90.8%) @5.2x, remaining 0:24 RBU 100.0% UBU  77.6%
 1397686272/1513308160 (92.4%) @5.3x, remaining 0:19 RBU 100.0% UBU  77.6%
 1422163968/1513308160 (94.0%) @5.3x, remaining 0:15 RBU 100.0% UBU  77.6%
 1446805504/1513308160 (95.6%) @5.3x, remaining 0:11 RBU 100.0% UBU  77.6%
 1470955520/1513308160 (97.2%) @5.2x, remaining 0:07 RBU 100.0% UBU  71.4%

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=4gms -use-the-force-luke=tracksize:738920 -use-the-force-luke=dao:738920 -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m
```

---

### Post by swarup on 2016-08-08
Don't know what the problem was there (DVD burning in above post), but I downloaded the iso onto the windows drive of the laptop in question, and was able to burn the disc without any issues. Plus, at bootup the DVD was immediately recognized, and Ubuntu loaded perfectly. I am now installing Ubuntu. Should go well.

---

### Post by Geoffrey_Arndt on 2016-08-08
Great News!    Let us know how the install goes.    From the specs, your laptop is running Intel graphics . . . a real plus re Linux compatibility "out of the box".   

Te DVD burn issue(s) . . . maybe particular dvd/brand,  . . . ?  Have not seen frequent failures at our ITL using high quality media and standard linux tools on ext3, 4 or ntfs file systems.

---

### Post by swarup on 2016-08-08
Everything worked out beautifully and the dual boot is now perfectly set up.

Only one question/issue for resolution: It was not stated in any of the websites I found giving guidance about this installation, that those using a laptop originally loaded with Windows 7, would be unable to install 16.04 using a bootable usb and would have to use a dvd. That should be clearly stated on all the How To sites, and it would thereby save huge time and spare one of unnecessary and useless struggle with the usb, which has become the standard tool for installation today.

---

### Post by swarup on 2016-08-08
Everything worked out beautifully and the dual boot is now perfectly set up.

Only one question/issue for resolution: It was not stated in any of the websites I found giving guidance about this installation, that those using a laptop originally loaded with Windows 7, would be unable to install 16.04 using a bootable usb and would have to use a dvd. That should be clearly stated on all the How To sites, and it would thereby save huge time and spare one of unnecessary and useless struggle with the usb, which has become the standard tool for installation today.

---

