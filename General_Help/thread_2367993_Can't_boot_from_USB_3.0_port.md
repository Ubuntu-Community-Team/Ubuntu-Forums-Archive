---
title: "Can't boot from USB 3.0 port"
date: 2017-08-05
forum: General Help
---

### Post by Kiki112 on 2017-08-05
[COLOR=#000000][FONT=HPRegular]I used Universal Usb Installer to install Ubuntu 16.04.3 on my 500 gb Toshiba Canvio[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular] [/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]When plug it in the 2.0 USB port, the hdd  boots normally[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]When plugged in the 3.0 port the light on the hdd doesn't flash and it doesn't boot[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular] [/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]I went into BIOS and set preOS 3.0 to enabled instead of auto[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]I tried disabling legacy, didn't help[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular] [/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Eventually when I was in BIOS one time, I noticed the HDD light did flash while plugged in 3.0, I have no idea how this was true[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular] [/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]I can't use a whole OS over a 2.0 entry, it's unusable.[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular] [/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]How do I boot from a 3.0 usb port?
I'm using an HP 350 G2, the i7 5500U version and 16GB RAM[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-08-05
It's probably just a USB 3 compatibility problem / also the installer could be at fault. Have you checked for a BIOS/firmware update for your motherboard? Are you willing to try booting to a Ubuntu 16.04 with a diferent instaler and see if the USB 3 problem gets any better? 
BTW I can boot via 3.0 USB here with very little noticable preformance, but I did not use Universal Usb Installer for the install.
My Specs:
```
inxi -SDM
System:    Host: me-750-417c Kernel: 4.13.0-041300rc2-lowlatency x86_64 (64 bit)
           Desktop: Xfce 4.12.3 Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop System: HP product: 750-417c v: 1.01
           Mobo: HP model: 828A v: 1.01 UEFI [Legacy]: AMI v: F.14 date: 09/19/2016
Battery    hidpp__2: charge: N/A condition: NA/NA Wh
Drives:    HDD Total Size: 3000.6GB (0.7% used)
           ID-1: /dev/sda model: WDC_WD5000AADS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD20EADS size: 2000.4GB
           ID-3: USB /dev/sdc model: 2115 size: 500.1GB
           Linux Foundation 3.0 root hub

```

---

### Post by Kiki112 on 2017-08-05
[IMG]https://image.prntscr.com/image/_yZLFeWqRnGm-QXEqzKlHw.png[/IMG]

These are the only updates recommended to me by the HP website upon typing in my serial number
[http://prntscr.com/g4uivx](http://prntscr.com/g4uivx)

BIOS update is not one of them, upon googling it suggests my BIOS is up to date if the HP website doesn't recommend a new one

I believe I had the same issue when trying to boot Window 7 from the same portable hard drive, it would boot from 2.0 but not from 3.0
So the issue probably isn't the ubuntu or the installer

---

### Post by Kiki112 on 2017-08-05
What I have noticed right now is that when preOS 3.0 is set to <Enabled> I wasn't able to boot from the 2.0 port either!
At least not automatically, I could boot if I pressed F9 (set boot order or something like that) and File explorer would open, I would navigate to EFI, boot and selected some file and it would boot
I ran disk check and it found 2 files
However, when preOS 3.0 was set to <Auto> Ubuntu would boot normally (from the 2.0 port).
And I tried again (because of the 2 files) and it would still wouldn't boot automatically if preOS 3.0 was set to <Enabled>

---

### Post by #&amp;thj^% on 2017-08-05
The only other advice I can add then is try booting in Legacy Mode...I just can't stand the way HP handles UEFI so I don't use it here at all.
I'm writing this booted from my USB drive now. (Please note the Specs)
```
inxi -DM
Machine:   Device: desktop System: HP product: 750-417c v: 1.01
           Mobo: HP model: 828A v: 1.01
         [COLOR="#FF0000"]  UEFI [Legacy]:[/COLOR] AMI v: F.14 date: 09/19/2016
Battery    hidpp__0: charge: N/A condition: NA/NA Wh
Drives:    HDD Total Size: 3500.7GB (4.3% used)
           ID-1: /dev/sda model: WDC_WD5000AADS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD20EADS size: 2000.4GB
           ID-3: USB /dev/sdc model: 2115 size: 500.1GB
          ** ID-4: USB /dev/sdd model: 00AACS size: 500.1GB**

```
This system running now:
```
inxi -S
System:    Host: me-pc Kernel: 4.12.4-1-ARCH x86_64 (64 bit)
           Desktop: Xfce 4.12.4 Distro: Arch

```
No noticeable performance loss at all.
Maybe someone else will chime in with a suggestion here.
Good Luck:)

---

### Post by Kiki112 on 2017-08-05
I'll try

When I was trying to install Ubuntu, I got a notification about something as the system is UEFI so it won't boot in BIOS mode, or something like that o.o
I clicked proceed anyway

Now Ubuntu won't start automatically (even from the 2.0 port), I now click F9 and pick EFI file and enter File explorer where I navigate to some file and press enter, which than starts Ubuntu
When the hdd is plugged into the 3.0 port there isn't anything inside the File explorer

---

### Post by Kris_M on 2017-08-18
> **Kiki112 said:**
> I'll try

When I was trying to install Ubuntu, I got a notification about something as the system is UEFI so it won't boot in BIOS mode, or something like that o.o
[SIZE=4]_**I clicked proceed anyway**_[/SIZE]

Now Ubuntu won't start automatically (even from the 2.0 port), I now click F9 and pick EFI file and enter File explorer where I navigate to some file and press enter, which than starts Ubuntu
When the hdd is plugged into the 3.0 port there isn't anything inside the File explorer

Therein lies your problem. Don't mistakenly boot a usb stick with a Ubuntu iso on it in uefi mode unless your system - at least the primary ssd/hd is uefi.
Redo that install.

---

### Post by kurt18947 on 2017-08-19
> **Kiki112 said:**
> [COLOR=#000000][FONT=HPRegular]I used Universal Usb Installer to install Ubuntu 16.04.3 on my 500 gb Toshiba Canvio[/FONT][/COLOR]



Is it necessary to use a USB installer to install to a USB hard drive? I don't know never having tried it but I thought that USB installers were intended to install to USB flash drives that come with FAT32 file systems by default. I may be off-base here, no expert.

---

