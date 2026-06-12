---
title: "Help with compiling driver"
date: 2006-07-15
forum: General Help
---

### Post by zxcvbnm on 2006-07-15
I have an Intergrated sound on my mobo but I don't have any sound....So I went and got the latest als driver from there site.

When compiling and typing "make" I get an error



****@ubuntu:~/alsa-driver-0.4.0$ make
make[1]: Entering directory `/home/harry/alsa-driver-0.4.0/support'

Support code were sucessfully compiled.

make[1]: Leaving directory `/home/harry/alsa-driver-0.4.0/support'
make[1]: Entering directory `/home/harry/alsa-driver-0.4.0/kernel'
gcc -DALSA_BUILD -I/usr/src/linux/include -I.. -E -D__GENKSYMS__ persist.c | /sbin/genksyms > ../include/modules/persist.ver
/bin/sh: /sbin/genksyms: No such file or directory
In file included from ../include/driver.h:50,
from persist.c:23:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
make[1]: *** [../include/modules/persist.ver] Error 127
make[1]: Leaving directory `/home/harry/alsa-driver-0.4.0/kernel'
make: *** [compile] Error 1
harry@ubuntu:~/alsa-driver-0.4.0$


Help is greatly appreciated

---

### Post by Ramses de Norre on 2006-07-15
Did ./configure run without any error? Is there anything in the READ_ME or INSTALL file about dependencies for compiling?

---

### Post by croak77 on 2006-07-15
> **zxcvbnm said:**
> 
/bin/sh: /sbin/genksyms: No such file or directory


You need the modutils package which provides genksyms. Also make sure you have the right linux kernel headers installed.

---

### Post by zxcvbnm on 2006-07-15
Thanks but know I get this error

****@ubuntu:~/alsa-driver-0.4.0$ make
make[1]: Entering directory `/home/harry/alsa-driver-0.4.0/support'

Support code were sucessfully compiled.

make[1]: Leaving directory `/home/harry/alsa-driver-0.4.0/support'
make[1]: Entering directory `/home/harry/alsa-driver-0.4.0/kernel'
gcc -DALSA_BUILD -I/usr/src/linux/include -I.. -E -D__GENKSYMS__ mixer.c | /sbin/genksyms > ../include/modules/mixer.ver
Usage:
genksyms [-dDwqhV] [-k kernel_version] [-p prefix] > .../linux/module/*.ver

  -d, --debug           Increment the debug level (repeatable)
  -D, --dump            Dump expanded symbol defs (for debugging only)
  -w, --warnings        Enable warnings
  -q, --quiet           Disable warnings (default)
  -h, --help            Print this message
  -V, --version         Print the release version
  -k ver
       --kernel ver     Set the kernel version for which we are compiling
  -p string
       --prefix string  Set a mangling prefix for all symbols
In file included from ../include/driver.h:50,
                 from mixer.c:23:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
make[1]: *** [../include/modules/mixer.ver] Error 1
make[1]: Leaving directory `/home/harry/alsa-driver-0.4.0/kernel'
make: *** [compile] Error 1


thanks

and BTW I am pretty sure ./configure went without a problem..

---

### Post by croak77 on 2006-07-15
> **zxcvbnm said:**
> Thanks but know I get this error

****@ubuntu:~/alsa-driver-0.4.0$ make
make[1]: Entering directory `/home/harry/alsa-driver-0.4.0/support'

Support code were sucessfully compiled.

make[1]: Leaving directory `/home/harry/alsa-driver-0.4.0/support'
make[1]: Entering directory `/home/harry/alsa-driver-0.4.0/kernel'
gcc -DALSA_BUILD -I/usr/src/linux/include -I.. -E -D__GENKSYMS__ mixer.c | /sbin/genksyms > ../include/modules/mixer.ver
Usage:
genksyms [-dDwqhV] [-k kernel_version] [-p prefix] > .../linux/module/*.ver

  -d, --debug           Increment the debug level (repeatable)
  -D, --dump            Dump expanded symbol defs (for debugging only)
  -w, --warnings        Enable warnings
  -q, --quiet           Disable warnings (default)
  -h, --help            Print this message
  -V, --version         Print the release version
  -k ver
       --kernel ver     Set the kernel version for which we are compiling
  -p string
       --prefix string  Set a mangling prefix for all symbols
In file included from ../include/driver.h:50,
                 from mixer.c:23:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
make[1]: *** [../include/modules/mixer.ver] Error 1
make[1]: Leaving directory `/home/harry/alsa-driver-0.4.0/kernel'
make: *** [compile] Error 1


thanks

and BTW I am pretty sure ./configure went without a problem..

Not sure. Is libc6-dev installed? I'm not sure if that would help or not. What motherboard/sound do you have?

---

### Post by zxcvbnm on 2006-07-15
I have an ASUS P5LD2 Deluxe motherboard it has a integrated sound with 7.1 surround sound support

And I have libc6-dev installed with the right headers

---

### Post by croak77 on 2006-07-15
> **zxcvbnm said:**
> I have an ASUS P5LD2 Deluxe motherboard it has a integrated sound with 7.1 surround sound support


Is it Intel HD audio? Or do you know the audio chipset?

---

### Post by zxcvbnm on 2006-07-15
It is Realtek

---

### Post by croak77 on 2006-07-15
> **zxcvbnm said:**
> It is Realtek

Post the output of:

```
lspci -v | grep audio
```

---

### Post by zxcvbnm on 2006-07-15
I get nothing with that command

But if I do it with out grep audio
I get this

```
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 81)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8178
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: dff00000-dfffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000eff00000
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81a0
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at dfbf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Capabilities: <available only to root>

0000:00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: dfe00000-dfefffff
        Capabilities: <available only to root>

0000:00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: dfd00000-dfdfffff
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at 6000 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 6400 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at 6800 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 66
        I/O ports at 7000 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 50
        Memory at dfbff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-0000afff
        Memory behind bridge: dfc00000-dfcfffff
        Prefetchable memory behind bridge: 0000000050000000-0000000050000000
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 2601
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 233
        I/O ports at 8800 [size=8]
        I/O ports at 8400 [size=4]
        I/O ports at 8000 [size=8]
        I/O ports at 7800 [size=4]
        I/O ports at 7400 [size=16]
        Memory at dfbffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: medium devsel
        I/O ports at 0400 [size=32]

0000:01:01.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
        Subsystem: Linksys Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 64, IRQ 225
        Memory at dfcdc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, medium devsel, latency 64, IRQ 74
        Memory at dfcdf800 (32-bit, non-prefetchable) [size=2K]
        Memory at dfcd8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:01:04.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (ASUS 8211 (ITE IT8212 ATA RAID Controller)) (rev 11)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8138
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 66
        I/O ports at a800 [size=8]
        I/O ports at a400 [size=4]
        I/O ports at a000 [size=8]
        I/O ports at 9800 [size=4]
        I/O ports at 9400 [size=16]
        Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 819f
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at dfdffc00 (64-bit, non-prefetchable) [size=128]
        Memory at dfdf8000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at b800 [size=128]
        Expansion ROM at dfd00000 [disabled] [size=512K]
        Capabilities: <available only to root>

0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 15)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet Controller (Asus)
        Flags: bus master, fast devsel, latency 0, IRQ 82
        Memory at dfefc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at c800 [size=256]
        Expansion ROM at dfec0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:05:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c2 (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0152
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at dffe0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at e000 [size=256]
        Expansion ROM at dffc0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:05:00.1 Display controller: ATI Technologies Inc: Unknown device 71e2
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0153
        Flags: bus master, fast devsel, latency 0
        Memory at dfff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

harry@ubuntu:~/alsa-driver-0.4.0$
```

---

### Post by croak77 on 2006-07-15
> **zxcvbnm said:**
> 


0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81a0
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at dfbf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>
]

That should be it. What you need is the hda-intel module. Is it loaded by default? Check the output of:

```
lsmod
```

---

### Post by zxcvbnm on 2006-07-15
Nope I don't see the module......

---

### Post by croak77 on 2006-07-15
> **zxcvbnm said:**
> Nope I don't see the module......

```
sudo modprobe snd-hda-intel
```

If you are running Breezy, I'm not sure if it will be there though. It might be easier to upgrade to Dapper rather try to compile for Breezy.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by zxcvbnm on 2006-07-15
I have Dapper....How would I get the hda-intel module though?...I see how to install the alsa driver but not the module in that link

and he is the outpur of the command

sudo modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.

---

### Post by croak77 on 2006-07-15
> **zxcvbnm said:**
> I have Dapper....How would I get the hda-intel module though?...I see how to install the alsa driver but not the module in that link

and he is the outpur of the command

sudo modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.

It works of my Dapper install. Are you sure everything is up to date. Also try to modprobe snd as well as soundcore.

---

### Post by zxcvbnm on 2006-07-15
Yes I upgraded to Dapper..Is there a way I can find out if I got everything from dapper installed?...Or a way to install the module?

---

### Post by croak77 on 2006-07-15
> **zxcvbnm said:**
> Yes I upgraded to Dapper..Is there a way I can find out if I got everything from dapper installed?...Or a way to install the module?

```
 dpkg --list alsa-base
```

What version is installed?

---

### Post by zxcvbnm on 2006-07-15
Here is the output...I think something is wrong

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alsa-base      1.0.10-4ubuntu ALSA driver configuration files

```

---

### Post by croak77 on 2006-07-15
Nope...that's the latest Ubuntu version. I don't why I can modprobe snd-hda-intel and you can't. Did modprobe snd and modprobe soundcore followed by snd-hda-intel do work? 

If not then try the link I gave you.

---

### Post by zxcvbnm on 2006-07-15
Wait what do you mean by modprobe soundcore ?

This command
sudo modprobe soundcore-hda-intel ?


And that link you gave just told how to install the driver but not the module?...DO you think If I put my breezy disk in I can get that module and update it to Dapper?

---

### Post by zxcvbnm on 2006-07-16
I did modprobe and got this

harry@harry-desktop:~/alsa-driver-1.0.4$ sudo modprobe snd-hda-intel
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/pci/hda/snd-hda-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.15-23-386/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
harry@harry-desktop:~/alsa-driver-1.0.4$

I just reinstalled Dapper..BTW

thanks to anybody that can help

---

