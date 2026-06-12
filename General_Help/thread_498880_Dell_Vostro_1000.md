---
title: "Dell Vostro 1000"
date: 2007-07-11
forum: General Help
---

### Post by involutaryhaxor on 2007-07-11
Im looking to buy a new (and slightly customized) Dell Vostro 1000 will play nice with Ubuntu. The only concern that I really have about compatibility is the wireless. I took a look to see if the same wireless card is used on any of the laptops on the linux section of their website, but it doesnt appear to be so. 

The options that I have for wireless on this laptop are the Dell Wireless 1390 which is the default choice and the Dell Wireless 1490. I am willing to pay the extra $10 for the 1490 if that means the difference between the wireless working and not. 

As for what I mean by compatible, I mean it either works after I install from the CD or someone gives me exact step-by-step instructions for how to make it work.

Thanks in advance!

---

### Post by borris.morris on 2007-07-16
I would bet it would work OTB, if not, then ndiswrapper is sure to get it working. I'm looking at the Vostro 1500, and sound is my most important (I have PCMCIA cards for wireless).

---

### Post by jsgarvin on 2007-07-18
Interesting that the Vostro 1000 only has those options. The other Vostros all have the Intel 3945 as an option for the Wireless, which is the same card that all the Ubuntu Dells come with.   Since the Ubuntu preinstalled laptops ONLY offer that wireless card, I'd be VERY hesitant to get anything else. I would guess there's a good reason that Dell doesn't offer the other's on the Ubuntu machines. I just ordered a Vostro 1700 myself, and made sure I picked the Intel wireless card for that very reason.

---

### Post by strabes on 2007-07-18
Yeah, make sure you get an intel wireless card; my dell has the 3945 abg and it works perfectly out of the box. It's unfortunate that they only offer the dell wireless ones with that laptop.

---

### Post by borris.morris on 2007-07-19
Sound?

---

### Post by mrcpu on 2007-07-30
I have 3 vostro 1000's.  Sounds works fine, wireless does not.  Havent' messed with NDISwrapper
yet.

---

### Post by Spam Banjo on 2007-09-07
> **borris.morris said:**
> Sound?

Sound is OK... Sound card sucks if you plan to use with guitar effects, etc. Couldn't get it to play the sound from microphone.

---

### Post by aka_mrcam on 2007-09-14
> **mrcpu said:**
> I have 3 vostro 1000's.  Sounds works fine, wireless does not.  Havent' messed with NDISwrapper
yet.

I just got my Vostro 1000 wireless working. I used [these]("http://ubuntuforums.org/showthread.php?t=297092") instructions but I downloaded the R151519.exe drivers from Dell. On the website it's under XP drivers and _WLAN.

---

### Post by Spam Banjo on 2007-09-17
I also got my Wireless working recently on my Vostro for Ubuntu AND OpenSuse.

For Ubuntu [I used this guide]("http://ubuntuforums.org/showthread.php?t=405990&highlight=dell+1390").

It doesn't get any easier than this. It's almost... dare I say it... Windows-Easy :-?

---

### Post by Rammdev on 2007-10-17
I can't seem  to get my wireless to work:

Dell Vostro

lspci:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)

I tried to follow the tutorial in the first post, but it didn't seem to work. Any help / tips

/edit
I followed the guide in the above post, and now everything works fine

---

### Post by mate84 on 2007-10-28
Hello,
I have a Dell vostro 1000 laptop with ATI 1150. In the restricted drivers manager I got this error: xorg-driver-fglrx is missing and after when I install it I get this information: fix broken packages first. And in the terminal:
mate@mate-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed. You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
mate@mate-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for mate:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
mate@mate-laptop:~$

At the moment I have large icons.....
Can anybody help me?

---

### Post by dyssident on 2007-12-15
For what its worth, I got wireless working on a Vostro 1500 with ease. For the Broadcom 4311 card, the drivers are distributed with Gusty, but it needs different firmware. 

1. Follow instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-c32709cb6de40e21b91790e33d349c111fcb83ec](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-c32709cb6de40e21b91790e33d349c111fcb83ec)
2. Open Restricted Drivers Manager and checked the option for "Firmware for Broadcom 43xx chipset family" and select the Download from the Internet option. 
3. Click on Network Manager icon and my networks should be there. No ndiswrapper!

---

### Post by Spam Banjo on 2007-12-17
> **dyssident said:**
> For what its worth, I got wireless working on a Vostro 1500 with ease. For the Broadcom 4311 card, the drivers are distributed with Gusty, but it needs different firmware. 

1. Follow instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-c32709cb6de40e21b91790e33d349c111fcb83ec](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-c32709cb6de40e21b91790e33d349c111fcb83ec)
2. Open Restricted Drivers Manager and checked the option for "Firmware for Broadcom 43xx chipset family" and select the Download from the Internet option. 
3. Click on Network Manager icon and my networks should be there. No ndiswrapper!

Thanks for that... :KS :KS :KS

For anyone who wants to know, he routine is exactly the same on a Vostro 1000 with Gutsy. A friend of mine has ordered a 1700 yesterday so I'll give you the low-down on that one soon too!

---

### Post by seipherdj on 2008-03-21
Ive been using a Vostro 1000 at work now for about 3 months. Ive had Kubuntu, Gentoo and now Debian Lenny installed on it.
Im satisfied(sort of). 
Compiz-fusion and the Fglrx driver on an Express200 card have caused alot of problems for me. There are just tones for artifacts(mainly on the cube) and screen tearing.

When running compiz if I have a konquer window open and then close it .... compiz dies.
If im running ktorrent and I close it while its fullscreen ... compiz dies.
Same thing with virtualbox(windowsXP guest) and most frustrating xscreensaver(which I think a bigger problem somehow linked with kpowersave and how it handles suspend and resume).

The Wireless works now without the ndiswrapper thanks to the 2.6.22 kernel and bcm43xx-fwcutter. But it is still very flaky, I cant get online in some venues that freinds or co-workers can who have intel based cards. Ive found that it will drop connection the first time I get and IP(I have to reaquire one before its a stable connection).

Overall this laptop has been good, cause its a company laptop and I didnt buy it.
At this point I wouldnt see any reason to go with an AMD .. ATI based laptop, its just caused me to much trouble.

I hope to buy a dellbuntu in the future , those 1420n's look sweet.

---

### Post by nbhat on 2008-03-26
I just got Dell Vostro 1000 and trying to install Ubuntu 7.1. When I boot with the CD (Desktop 64 bit) it hangs after running the boot scripts (this is just after the check for battery). Monitor blinks couple times before everything stops. But I am able to access the command prompt using Alt + Function keys. But no graphic display. Has anybody faced similar problem or can any one give pointers to diagnose the issue.

thanks

---

### Post by nbhat on 2008-03-26
I managed to start it using safe graphics made. But now at the time partition I am getting only 2 options. Using the entire disk or Manual. I am not getting resize partition option. I am trying to set up a dual boot system and I got the machine with 2 partitions one main and other recovery partitions is this causing the issue ?

---

### Post by Spam Banjo on 2008-03-27
> **nbhat said:**
> But now at the time partition I am getting only 2 options. Using the entire disk or Manual.

I had the same issue with a brand new Vostro 1000, although I was confident enough to proceed with manual setup. Everything installed OK and I was left with a dual boot Vista / Ubuntu machine.

Manual worked fine for me, but of cause, I would not recommend this unless you are confident with Manual Settings, and you have backed up important info in case of any installation or boot issues you may receive (obviously errors may occur if your machine has hardware issues).

---

### Post by nbhat on 2008-03-28
I shrunk the C drive using Vista disk management and then I selected the option to use free space while installing. 

Thanks for the inputs.

---

### Post by Spam Banjo on 2008-03-28
> **nbhat said:**
> I shrunk the C drive using Vista disk management and then I selected the option to use free space while installing. 

Thanks for the inputs.

Congratulations!!!

Windows disk management never ever works for me!!! lol

---

