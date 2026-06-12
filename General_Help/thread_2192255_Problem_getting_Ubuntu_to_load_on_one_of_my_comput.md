---
title: "Problem getting Ubuntu to load on one of my computers"
date: 2013-12-06
forum: General Help
---

### Post by mmcl26554 on 2013-12-06
I have a computer (actually 2 of them) which don't seem friendly to Ubuntu.   That is, it takes a full 3-4 minutes to load.  It seems to spend 2 minutes doing nothing, not even logging any activity and then one minute loading.    I have tried dealing with this problem on this forum but nothing has helped.   Once loaded it works just fine.   I want to try a different version of Linux to see if it is just Ubuntu or all Linux distros.    So far I have tried Deepin, which was a little faster by about a minute.  It is beautiful and I like but the support in mandarin is tough to read, and there is at least one thing that doesn't work properly, Hibernation, works from terminal but won't put in the menu to click on.   I have tried Zorin but it takes 4.5 minutes to boot.   Mint is slightly less than 3 minutes.   However, these are all based on Ubuntu. Since I am a Linux beginner I don't know a lot about other flavors of Linux.   So could someone suggest other flavors to try which are not Ubuntu or Debian based that would be easy to load from either a disk or USB flash drive.
Michael

---

### Post by DuckHook on 2013-12-06
Hi Michael,

In cases such as yours, it is helpful to:

1. Give us far more HW specs. Can't tell if your load times are typical for your HW. Need the following: CPU, RAM, Video Chipset/GPU, Disk controller and HDD size, VRAM, NIC &/or WIFI chipsets.

2. Take a look through your logs, esp syslog. Ubuntu comes with a log viewer that makes going through your logs much easier than what we used to have to do. Or you can use a text editor and simply load in syslog, found at /var/log/syslog. Syslog has dates/times beside each entry, so it's relatively easy to see which process is hogging your load times. You may wish to leave your computer off for an hour so that the time entries are separated enough from your last session that they are easy to differentiate. Note that syslog can be huge, so be prepared to go through some significant parsing.

---

### Post by mmcl26554 on 2013-12-06
I'll look into the sys log later.   I did try a program which did a graphical representation of the boot process but it didn't seem to include the first 2 minutes.  However, I'm happy to have another try at it. By the way I am using a dedicated disk for Linux 80 Gb and at the time it is the only disk as Grub would never work as a dual boot as it wouldn't boot Vista.   I worked with the Boot repair people but we could never get it to boot Vista.  So my solution was to install Linux on its own disk and select which OS to boot with the F10 key during the boot process.  
Here is a copy of the specs:
```
[TABLE]
[TR="bgcolor: #000000"]
[TH="align: left"][SIZE=-1][COLOR=#ffffff]Feature[/COLOR][/SIZE][/TH]
[TH="align: left"][SIZE=-1][COLOR=#ffffff]Specification[/COLOR][/SIZE][/TH]
[/TR]
[TR]
[TD]Processor[/TD]
[TD]Intel® Core&#8482;2 Duo T5250 dual core processor
[LIST]
[*]Each core operates at 1.5 GHz
[*]Shared 2 MB L2 cache
[*]667 MHz front side bus
[/LIST]
[/TD]
[/TR]
[TR]
[TD]Chipset[/TD]
[TD]Intel GM965[/TD]
[/TR]
[TR]
[TD]Memory[/TD]
[TD]Installed: 2048 MB DDR2, 667 MHz (PC2-5300) SO-DIMM (two 1024 MB memory modules)
Expandable to: 4 GB (two dual channel capable slots support module sizes up to 2 GB)[/TD]
[/TR]
[TR]
[TD]Hard Drive[/TD]
[TD]320 GB, 7200 RPM SATA II[/TD]
[/TR]
[TR]
[TD]Optical Drive[/TD]
[TD]8X super multi-format DVD +/- RW dual layer drive (up to 8.5 GB)
[LIST]
[*]Write max: 8X DVD+R, 8X DVD-R, 4X DVD+R DL, 4X DVD-R DL, 8X DVD+RW, 6X DVD-RW, 5X DVD-RAM, 24X CD-R, 24X CD-RW
[*]Read max: 8X DVD-ROM, 24X CD-ROM
[*]Slot load, slim form factor
[/LIST]
[/TD]
[/TR]
[TR]
[TD]Media Card Reader[/TD]
[TD]5-in-1 media manager supports the following memory card types:
[LIST]
[*]xD-Picture Card&#8482; (xD)
[*]Secure Digital&#8482; (SD)
[*]Secure Digital HD (SD-HD)
[*]Mini Secure Digital (Mini SD; adapter needed)
[*]MultiMedia Card&#8482; (MMC)
[*]Reduced Size MultiMedia Card (RS-MMC; adapter needed)
[*]MultiMedia Card Plus (MMC Plus)
[*]Memory Stick&#8482; (MS)
[*]Memory Stick Pro (MS Pro)
[*]Memory Stick Duo (MS Duo)
[*]Memory Stick Pro Duo (MS Pro Duo)
[*]Memory Stick MagicGate
[*]Memory Stick MagicGate Duo
[/LIST]
[/TD]
[/TR]
[TR]
[TD]Video[/TD]
[TD]Integrated Intel Graphics Media Accelerator X3100[/TD]
[/TR]
[TR]
[TD]TV Tuner[/TD]
[TD]External analog/digital TV tuner with 3-D Comb (USB)
Ports:
[LIST]
[*]One analog TV
[*]One ATSC antenna
[*]Two RCA stereo audio jacks (left and right channel)
[*]One RCA video jack
[*]One S-Video
[/LIST]
[/TD]
[/TR]
[TR]
[TD]Sound[/TD]
[TD]Integrated 8-Channel (7.1) High Definition audio[/TD]
[/TR]
[TR]
[TD]Network[/TD]
[TD]Integrated 10/100/1000 Mbps Ethernet LAN
802.11n (pre-n) tri-band wireless LAN (compatible with 802.11 a/b/g/n)[/TD]
[/TR]
[TR]
[TD]Modem[/TD]
[TD]External USB 56K ITU V.92 ready fax/modem[/TD]
[/TR]
[TR]
[TD]Monitor[/TD]
[TD]Integrated 19-inch widescreen TFT active matrix display[/TD]
[/TR]
[TR]
[TD]Speakers[/TD]
[TD]Integrated NXT SoundVu acoustic front panel speaker technology[/TD]
[/TR]
[TR]
[TD]Expansion Slots[/TD]
[TD]MiniCard slots (one used by wireless LAN card)[/TD]
[/TR]
[TR]
[TD]Peripheral Connectors[/TD]
[TD]Main computer unit:
[LIST]
[*]One Memory card reader slot (see Media Card Reader information above)
[*]One IEEE 1394 (FireWire&#8482;) port
[*]Three USB ports
[*]One Headphone jack
[*]One Microphone jack
[/LIST]

AC Adapter:
[LIST]
[*]One RJ-45 LAN port
[*]Four USB 2.0 ports
[*]One IR blaster connector
[*]One optical digital audio out connector
[*]One coaxial digital audio out connector
[*]One power/Data cable connector (main unit cable)
[*]One AC power connector
[/LIST]
[/TD]
[/TR]
[TR]
[TD]Power Supply[/TD]
[TD]180 watt power adapter with peripheral connectors (see information above)[/TD]
[/TR]
[TR]
[TD]Input Devices[/TD]
[TD]Gateway One premium wireless multimedia keyboard
River Rock wireless optical mouse
Gateway One Media Center remote control
1.5 megapixel Web cam[/TD]
[/TR]
[/TABLE]

```

---

### Post by DuckHook on 2013-12-06
Is this a Windows readout? It doesn't seem to have the same depth given by the classical Linux commands. I don't see a 80GB HDD here. Is it connected through USB? If so, is it USB v1? Again, if so, this would be the source of your slow boot times. USB v1 is very slow. Even USB v2 is slow compared to SATA2. The rest of your system looks fine and can run Ubuntu easily . No obvious chokepoints except the USB.

---

### Post by mmcl26554 on 2013-12-06
The Linux drive is an SATA drive and is 80Gb installed in the computer and the only drive at the time of install.   Later I put the Vista drive back in and select the drive to boot from with the F10 key.   So as far as Linux is concerned it thinks it is the only OS in the system.    The specifications I posted are from the Gateway website.   Currently the computer only has the Linux drive in it and is not on, I am using my HP notebook to post at present.   You are correct in concluding the computer should run Ubuntu or Linux just fine.  We established that in my other postings in another thread.   But for some reason it doesn't and so far it is a mystery.   I have a disk with "Dragara Linux" I thought I would try it just to see what happens with it.   I will post back the results of this.
Michael

---

### Post by DuckHook on 2013-12-06
If you wish to experiment with different distros to measure loading speeds, then here are some non-Ubuntu-based distros that are quite popular.

Fedora
Sabayon
Debian
CrunchBang
Chakra
PCLinuxOS
Mageia
openSUSE
Slackware

I doubt that you will have good results with Fedora or Sabayon. I find them the slowest of all distros—slower even than the various Ubuntus—but you can try them out for yourself. CrunchBang is blazingly fast, but has an environment that most people find odd and difficult to get used to. I'm happy with it, but then, I'm a bit of a magpie. Debian is rock solid and stable, but rather unexciting. openSUSE is a pretty big distro. So is Slackware. They load relatively quickly on my systems. Mageia and PCLinuxOS are based on or forked from Mandriva which has gone through a roller-coaster ride of relevance including going into and out of bankruptcy. Some people avoid these variants because of concerns over long term support, but I find such worries odd, since it is so easy to move to other distros in the Linux-sphere that concerns like lock-in are not nearly as significant as they are with proprietary jailware. This leaves Chakra. Of all the full-bodied distros, this has to be my favourite outside of the Ubuntu variants. It's a fork of Arch, so it is relatively well-tested and stable. It is fast and looks gorgeous, has a decent package manager, and if you can get used to kde, it works very intuitively. It is pure kde though, so if you don't like kde, don't even start. Its only drawback would be its small user base and the fact that it is the least-used distro among the above.

I've stayed away from minimalist but super fast distros on the assumption that you are looking for a full desktop experience.

---

### Post by mmcl26554 on 2013-12-06
DuckHook,
I'm downloading Chakra as I write.   I'll give it a shot.   Since I have nothing to lose, and being a beginner I have little knowledge about the various GUI's.    I did impairment with RedHat about 15 years ago and it had a few different GUI's but I didn't see much difference in them and I do remember KDE was one of them.   Like I said I did like the Deepin desktop but the support and forums had a lot of mandarin which I can't read, so that really isn't a viable option.   It would be nice if I could install Deepin's GUI in Ubuntu but I understand that is not possible.   So I'll see how I like Chakra.   Thanks for the rapid responses.
Michael

---

### Post by mmcl26554 on 2013-12-07
I installed [COLOR=#000000]Chakra and it booted in 1.5 minutes.   So there is something about Ubuntu and Ubuntu based distros that the Gateway GZ7112 and GZ7108 don't like!   There is a lot to learn to run Chakra and will be a bit more of a challenge than Ubuntu.   Like, smb.conf,  I was able to edit it to put in my workgroup's name but couldn't find the name resolver.   So I couldn't get to my network drive.   I'll have to find a tutorial on [/COLOR][COLOR=#000000]Chakra and work on things.    My 72 yo mind can use the stimulation.   Since I am retired it has less to worry about and can get lazy.
Michael[/COLOR]

---

### Post by DuckHook on 2013-12-07
I believe that Chakra has a small but vibrant forum community. You will also find the Arch forums very helpful. Though forked, Chakra has not diverged from Arch very far yet and most of the fixes and tweaks that apply to the one apply to the other.

Good luck and Happy Linuxing!

---

### Post by mmcl26554 on 2013-12-07
The general look of Ubuntu I like better, however, I suppose there is a lot of tweaking that can be done with Chakra which I'll have to learn.    I still wonder why Ubuntu and Ubuntu based distros don't boot well on this computer.   I don't you have any incite to what could be the cause.    I have looked into some logs but they don't show the first 2 minutes when Ubuntu is just thinking and waiting for something.    I haven't yet looked into syslog but will, but to do that I'll have to load another drive with Ubuntu, I think I have one around here someplace I can use.  But again thanks for your guidance, rest assured I'll be back with more questions.
Michael

---

### Post by mmcl26554 on 2013-12-24
I loaded 14.04 alpha and it actually loaded in 2 minutes instead of 3 like the other versions.   Still no idea why this computer takes so long to load.   But I can live with it.
Michael

---

