---
title: "gparted-live CD does not run on my old PC"
date: 2022-11-27
forum: General Help
---

### Post by kuen2 on 2022-11-27
Old PC :  Acer aspire M5700
MB : G45T AM2 V:1.0
BIOS : American Megatrends V 02.16

The HDD is burnt, literally, and motherboard damaged.  Cannot install new OS on this PC because Windows installer finds no any hard drive drivers, including USB hard drives.  The only drive still works on this old PC is the ODD, a DVD drive.

Have downloarded gparted-live-1.4.0-6-i686 and burnt to a CD. But it does not run on the above said old PC. 

Please help to get an Ubutu live OS on CD run on this old PC.
Thank you.

---

### Post by MAFoElffen on 2022-11-27
> **kuen2 said:**
> Old PC :  Acer aspire M5700
MB : G45T AM2 V:1.0
BIOS : American Megatrends V 02.16

The HDD is burnt, literally, and motherboard damaged.  Cannot install new OS on this PC because Windows installer finds no any hard drive drivers, including USB hard drives.  The only drive still works on this old PC is the ODD, a DVD drive.

Have downloarded [COLOR=#ff0000]gparted-live-1.4.0-6-i686[/COLOR] and burnt to a CD. But it does not run on the above said old PC. 

Please help to get an Ubutu live OS on CD run on this old PC.
Thank you.
Your processor is an old iCore 2 Duo Quad... You should have downloaded the 64bit version: [gparted-live-1.4.0-6-amd64.iso]("https://downloads.sourceforge.net/gparted/gparted-live-1.4.0-6-amd64.iso")

You say that most everything is fried. What are you hoping for? Salvageable parts to try on another motherboard?

---

### Post by kuen2 on 2022-11-27
Thank you.

Sorry for not providing enough data of the PC.
CPU: Intel Core2 Quad CPU&#65292;still good.
RAM: DDR2 800 SDRAM 4G&#65292;still good.
GPU: Removed, now use on board Intel® G45.
PSU: Liteon 6301-08Ak, still good.
MB : G45T AM2 V:1.0, still good except for Windows installer finds no hard drive drivers.


Since 2015, the PC was used for only for 1.storing some secondary backup, and 2.news and music on Youtube. 
I hope a live CD can provide a simple function for the PC to run Google Chrome. 


From the very begining, the PC is a 32bit one. Why 64b. when it comes to use a live CD?

---

### Post by TheFu on 2022-11-28
Ubuntu doesn't come in 32-bit since 2019.

The gparted live CD isn't an official Ubuntu version, BTW.

If there isn't any storage working in the system, there's little point in having gparted.

For that system, you'd be better off putting an Lubuntu 20.04 or 22.04 onto a flash drive and booting that.  If that doesn't work, check the BIOS to verify it isn't trying to use RAID. AHCI is the mode required for disks to work.  Plus, with Lubuntu, the older iGPU will be less stressed and I suspect there's a gparted or something similar built into the release.  I haven't used Lubuntu since around 2014, so I don't know for sure.

The G45 era has some terrible video.  Back when I had a MB like that, it couldn't support more than DVD quality video. No 720p worked without massive stuttering.

---

### Post by kuen2 on 2022-11-28
Thank you.


"Ubuntu doesn't come in 32-bit since 2019."
Any live cd comes in 32-bit now?


"The gparted live CD isn't an official Ubuntu version, BTW."
Don't know much about Ubuntu or gparted live CD. I found it by Google Search. Download it because of its size, only around 600mb.  I can put it on a 700mb CD. I cannot even find it today.




"If there isn't any storage working in the system, there's little point in having gparted."
Do you mean there is little point in having any live CD?  All I hope is to get Google Chrome working on the PC. 


"For that system, you'd be better off putting an Lubuntu 20.04 or 22.04 onto a flash drive and booting that."
Well, does Lubuntu 20.04 run on a 32b. PC?
The burn-accident damaged the drivers for hard drives, including flash drive. BIOS does not recognize hard drive, including flash drive, and therefore, the PC cannot boot anything on any hard drive and/or flash drive.  Except for ODD, BIOS recognizes the ODD and therefore, live CD can get the PC running.


"AHCI is the mode required for disks to work."
Yes. It is set at AHCI.


"Plus, with Lubuntu, the older iGPU will be less stressed and I suspect there's a gparted or something similar built into the release."
I really don't know what to use except that I think a live CD can do the trick.

---

### Post by TheFu on 2022-11-28
> **kuen2 said:**
> "Ubuntu doesn't come in 32-bit since 2019."
Any live cd comes in 32-bit now?

Not from Ubuntu. You'll need to check other distros, but these are the "Ubuntu Forums" and you posted in the "Ubuntu Official Flavours" subforum.  If I were guessing, it would be a debian version.

> **kuen2 said:**
> "The gparted live CD isn't an official Ubuntu version, BTW."
Don't know much about Ubuntu or gparted live CD. I found it by Google Search. Download it because of its size, only around 600mb.  I can put it on a 700mb CD. I cannot even find it today.
The gparted distro is a minimal release primarily for gparted.  I've used it, but only for that purpose. I don't know if it comes with anything else.  If you want a small distro, I know TinyCore comes in 12MB - 128MB sizes, but it is a little odd. The package manager for it is strange. It is not debian-based, so no APT.


> **kuen2 said:**
> "If there isn't any storage working in the system, there's little point in having gparted."
Do you mean there is little point in having any live CD?  All I hope is to get Google Chrome working on the PC. 

No.  gparted is a disk partitioning tool.  If you don't have disks, you don't need to partition anything. Useless.  To my knowledge, no distro comes with proprietary Google Chrome. I think that's an unrealistic expectation.  I haven't used Chrome except where mandated - on proprietary google hardware like a Chromebook or Android phone.  On Linux, when a chrome-like browser, I'll use Chromium.  It is the base browser that Chrome is built from and a separate F/LOSS project. It can't do everything that Chrome does, but it is shipped in some distros.  It would likely be a security failure at this point since they stopped shipping Chromium as a debian package a few years ago and only provide it as a snap package.  Without any storage, that snap package shipped in the ISO will always be out of date.


> **kuen2 said:**
> "For that system, you'd be better off putting an Lubuntu 20.04 or 22.04 onto a flash drive and booting that."
Well, does Lubuntu 20.04 run on a 32b. PC?
The burn-accident damaged the drivers for hard drives, including flash drive. BIOS does not recognize hard drive, including flash drive, and therefore, the PC cannot boot anything on any hard drive and/or flash drive.  Except for ODD, BIOS recognizes the ODD and therefore, live CD can get the PC running.

I don't know.  BTW, I have zero idea what an "ODD" is.  Web searches say it is "Oppositional defiant disorder".

> **kuen2 said:**
> "Plus, with Lubuntu, the older iGPU will be less stressed and I suspect there's a gparted or something similar built into the release."
I really don't know what to use except that I think a live CD can do the trick.
Neither do I.  I suspect your old PC is done. For the cost of a nice date/dinner with my wife, a used PC can be purchased.  Around here, they can be found for $75.  We each have different levels of hassle we are willing to attempt to make something work.  A PC that doesn't have any writable storage wouldn't rate high for my effort.  Tiny Core is sometimes used for "diskless" systems.
[https://itsfoss.com/32-bit-os-list/](https://itsfoss.com/32-bit-os-list/) was found by a web search. It lists 32-bit OSes. That list has MX Linux, Debian, and Tiny Core.  A few friends run MX Linux off USB flash drives and are mostly happy.  I've used TinyCore for years for special needs.  Debian is what Ubuntu feels like the most, so if you know Ubuntu, that would probably be the least hassle. If not, Tiny Core is the smallest ... just pick the level of bloat you want. They have a minimal (12mb), standard (64MB) and bloated (120mb) versions.

---

### Post by MAFoElffen on 2022-11-28
I am sorry, but Intel Core 2 Quad [COLOR=#ff0000]IS[/COLOR] 64bit. That motherboard says it supports 64bit. You can run a 64bit OS or 32bit OS. (Ubuntu flavors no longer support 32bit...)

BUT... That motherboard is too old to boot from a USB. The original PC had a CD drive right? 

Do your have a DVD drive? That is what you would need, because a current Ubuntu flavor LiveCD will not fit on a CD.

---

