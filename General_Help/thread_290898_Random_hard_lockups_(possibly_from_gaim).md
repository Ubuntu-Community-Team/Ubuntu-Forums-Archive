---
title: "Random hard lockups (possibly from gaim)"
date: 2006-11-01
forum: General Help
---

### Post by LenzM on 2006-11-01
I get random hard lockups and the only common factor seems to be that gaim is running every time.  I used to leave gaim running and would come to work the next day to find it locked up, I started closing gaim when I left and this stopped.  I also get the lockups while I'm using the computer at seemingly random times (when gaim is running).  I'm not positive that gaim has been running every time, but it has been running the past 10-15 times since I've been checking.  Sometimes I'll go a week plus without a lockup but other times I'll get a couple in a day.

This happened when I was using dapper also, so it's not an edgy upgrade issue.  I was using 1.5.0 with dapper, then tried 2.0beta4 and am now using 2.0beta3 from the edgy repo.
A coworker has a very similar setup, with different video cards, and also gets the lockups.  
They have occurred on relatively clean installs of both ubuntu and xubuntu. 
I've run memtest and found no problems. 

Specs
Procs: Dual AMD Athlon(tm) MP 2000+
RAM: 4 Sticks of Crucial 512MB
Video Cards: nvidia NV11 [GeForce2 MX/MX 400], nvidia NV5M64 [RIVA TNT2 Model 64/Model

Other stuff frequently running
Firefox
Thunderbird
vmware player/workstation
eclipse
amarok
gnome-terminal
mysql
ssh

I haven't been able to find anything in the forums or searching the web, so if anyone knows what's wrong or someone else that has had similar problems any help would be appreciated.

---

### Post by LenzM on 2006-11-03
Anyone.

Even completely unsubstantiated reasons would be welcome.  Then at least I'd have somewhere to start.

---

### Post by Ninjagecko on 2006-11-06
Comment 1:
As you commented on my thread at [http://www.ubuntuforums.org/showthread.php?p=1697271](http://www.ubuntuforums.org/showthread.php?p=1697271) , I too have been experiencing similar lockups. It seems one of the apps you said is often running is Amarok.... Maybe it's Amarok?

Comment 2:
Try not running Gaim and see if you no longer experience lockups? Apply some scientific process: only run a single program (or very few) programs at once and see whether you experience lockups or not. Perhaps you might experience lockups without any programs running? (You do say it happens when you aren't at the computer...)

If it's really Gaim, you can use another chat client. Kopete used to be buggy and is now tolerable, and has a host of useful almost-implemented features and great customization (though it once deleted my entire server-side AIM buddy list, but they put in -- albeit by accident -- a safeguard against it, and have been trying to fix this bug for the last few months).

Comment 3:
Perhaps the symptoms of these lockups might provide some clue. (e.g. If your screen has gone completely black and won't wake up, maybe it's a powersaving problem.)


(try ctrl-alt-f1 as usual when you next get your lockup -- unless you really meant an honest-to-goodness hard lockup)

---

### Post by LenzM on 2006-11-06
I have definitely had the freezes without amarok running.

I have been testing it pseudo-scientifically - in the past month or so I have not experienced any lockups when I'm not using gaim, and have had about 10 while using it.  Since this is at work, I can't sit there with just gaim open (too bad).

When the lockups occur while I'm using the computer, it completely stops responding to the keyboard(ctrl-alt-f1, ctrl-alt-backspace) and mouse and the display is frozen.  When I was finding it frozen when returning to work, the screen just stayed black and didn't respond.

This is an honest-to-goodnes hard lockup, I've let it sit there for 20 minutes and not a thing changed.  It doesn't respond to ping or ssh.  My linux-using coworkers and I have no idea why this is happening.

---

### Post by Nozem on 2006-11-06
Hi,

just a quick word to let you know I'm having these random lockups as well, although I'm not running Gaim. At first I thought it might have something to do with me running Beryl, although the problem persists when I use Metacity as well.

---

### Post by dannyboy79 on 2007-01-02
I am experiencing this problem now as well. I run Dapper with Gaim as well. I have had this happen about 2-5 times in the last 2 weeeks now and it all of sudden started happening and I can't think what I changed???! I can't ssh into it and it doesn't respond to pings. It's just a black screen and nothing will make it come back excpet for a reset on the main box. I have a CPU0: Intel(R) Celeron(R) CPU 2.66GHz stepping 09
 with the stock fan, i thought of heat and took the side of the case off but it still happened so I believe we can rule out heat issues. I have a 420W power supply, 1.5GB ram on foxconn motherboard with a brand new updated bios! Ah hah, this actually might be it! I am going to go back to the original bios and make gaim run all the time and see what happens to rule out the bios issue. I installed the latest bios due to my sound only wrking out  of the left speaker and can't figure out why this is. Anyway, I'll post back my findings so we can narrow this down. I run 2.6.15-27-686 kernel. this is what lspci -v says:
 sudo lspci -v
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [c0] AGP version 3.5

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 128, IRQ 5
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 4000 [size=16]
        Capabilities: [58] Power Management version 2

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at e000 [size=256]
        I/O ports at e800 [size=128]
        Capabilities: [48] Power Management version 2

0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at eb027000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at eb028000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at eb029000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 7002
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at eb024000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at e400 [size=256]
        Memory at eb025000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 70000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2

0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01) (prog-if 85 [Master SecO PriO])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        I/O ports at e900 [size=8]
        I/O ports at ea00 [size=4]
        I/O ports at eb00 [size=8]
        I/O ports at ec00 [size=4]
        I/O ports at ed00 [size=16]
        I/O ports at <unassigned>
        Capabilities: [58] Power Management version 2

0000:00:08.0 FireWire (IEEE 1394): Texas Instruments FireWire Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Texas Instruments: Unknown device 8010
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at eb026000 (32-bit, non-prefetchable) [size=2K]
        Memory at eb020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 1

0000:00:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR-350
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc.: Unknown device 2144
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 5
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0

---

### Post by LenzM on 2007-01-02
I've recently been getting the lockups without gaim running, so it's not that.

We (my fellow linux using coworkers and I) are now speculating that it's probably some driver-hardware issue since something has to be happening at the kernel level to cause hard locks with no logging.  Of course that's just speculation.

---

### Post by m2.g5ru6y7s on 2007-02-03
I have also the same symptoms.
Ubuntu seems to lockup (freeze is a better term) completely
I have now version 6.10 of Ubuntu.
It happens random, so it is very hard to reproduce.
Maybe it is the hardware, but it is very hard to check because it is a laptop.
Hardware:
Acer Aspire 1700
Video card: nVidia FxGo5600 using:
NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746
memory: 2Gb
networkcard: SiS 900 PCI Fast Ethernet at 0x2000, IRQ 217
harddisk:Maxtor 6Y120L0, ATA DISK drive (120Gb)

---

### Post by m2.g5ru6y7s on 2007-02-04
I forgot to mention in my previous message that I had always dual screen when the crash occurred. I'm now testing the  1.0-9746 driver single screen & till now it goes well...

---

### Post by dannyboy79 on 2007-02-05
hey guys, I just noticed that m2.g5ru6y7s has the same ethernet card as I do. it's built onto my foxconn motherboard but  it's the SiS900 PCI Fast Ethernet chipset. We should try to find a common link between all our hardware if we want to troublehsoot this effectively. Why doesn't everyone post their lspci -v output like I did.

---

### Post by Chyper on 2007-02-05
i've the same problem :/
i am not running gaim
my comp specs
intel d101GGC
intergrated x200
512 mb ram
p 805d
74 gb sata raptor

uname -r  - 2.6.15-27-686

lspci -v

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a33 (rev 01)
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at <ignored> (64-bit, non-prefetchable)

0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: [b0] #0d [0000]

0000:00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 177
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at 20000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 185
        I/O ports at fa00 [size=8]
        I/O ports at f900 [size=4]
        I/O ports at f800 [size=8]
        I/O ports at f700 [size=4]
        I/O ports at f600 [size=16]
        Memory at fe02e000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at 20080000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
        Subsystem: Intel Corporation: Unknown device d600
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Memory at fe02a000 (32-bit, non-prefetchable) [size=1K]

0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at f400 [size=16]
        Capabilities: [70] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, slow devsel, latency 64, IRQ 193
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: fdc00000-fdcfffff

0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a61 (prog-if 00 [VGA])
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 217
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at ee00 [size=256]
        Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fde00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Intel Corporation: Unknown device d600
        Flags: bus master, medium devsel, latency 64, IRQ 209
        I/O ports at de00 [size=256]
        Memory at fddff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

---

### Post by nicesnake on 2007-04-02
I have very similar configuration to dannyboy79's , and i'm also experiencing hard lockups (now on feisty , but i had this issue on all versions) , usually when cpu usage is high (compilations, unpacking large archives) i managed to reduce lockups by lovering bus speed a little (and so on cpu from 2.80 to around 2.68 ) 

my lspci 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
        Subsystem: ASRock Incorporation Unknown device 0661
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: cfd00000-cfefffff
        Prefetchable memory behind bridge: bfa00000-cfbfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 0c00 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: ASRock Incorporation Unknown device 5513
        Flags: bus master, medium devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ff00 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASRock Incorporation Unknown device 7012
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at cfff9000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 3
        Memory at cfffa000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 7002
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASRock Incorporation Unknown device 0900
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at d400 [size=256]
        Memory at cfff8000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: ASRock Incorporation Unknown device 6330
        Flags: 66MHz, medium devsel, IRQ 11
        BIST result: 00
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        Memory at cfee0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at bc00 [size=128]
        Capabilities: <access denied>


vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.80GHz
stepping        : 9
cpu MHz         : 2683.204

---

### Post by Spectre5 on 2007-04-16
Anyone ever find a solution?

I also have this problem....random freezes/lock-ups....it it really getting annoying!  I never thought windows would be more stable on my machine that linux!  Lets find the root of this problem.
 
Here is my lspci -v


00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
        Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Unknown device b165
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 3
        Memory at 44000000 (32-bit, prefetchable) [size=64M]
        Memory at 40100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-400fffff
        Prefetchable memory behind bridge: 20000000-200fffff

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corporation 82801AA IDE
        Flags: bus master, medium devsel, latency 0
        I/O ports at 2020 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation 82801AA USB
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at eec0 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
        Subsystem: Intel Corporation 82801AA SMBus
        Flags: medium devsel, IRQ 5
        I/O ports at eee0 [size=16]

01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
        Subsystem: Compaq Computer Corporation Unknown device b19d
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 1000 [size=256]
        Capabilities: <access denied>

01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 3
        I/O ports at 1400 [size=256]
        Memory at 40000000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 01 [Hayes/16450])
        Subsystem: PCTel Inc Unknown device 0001
        Flags: medium devsel, IRQ 11
        I/O ports at 1800 [size=64]
        Capabilities: <access denied>

---

### Post by Spectre5 on 2007-04-17
btw...

I get these random freezes too...any have any ideas? Mine even happen when I am not using the computer (i.e. I leave it on, turn off the monitor, then come back and turn the monitor on to find my frozen screen underneath).

These happen randomly for me and I am using xubuntu 6.10. The only way I have been able to replicate these reliably is via Scite...load a .c file, click compile, then try to resize the scite window = freeze. It freezes as soon as I click the resize corner thing....I was unable to get useful help regarding this at the scite bug reporting site. Although it may be a scite problem, I also get the same freezes when not using scite....randomly.

---

### Post by dannyboy79 on 2007-04-18
yeah, I have never been able to lock this down to anything specific. I sometimes have lockups when transferring large files thru samba or ftp and also trying to do other stuff. i would hate to think that my mchaine can't handle more than a couple things at once. actually I know that not it becuase I have a 650W PSU, ASRock 775dual-VSTA, Intel Core 2 Duo E4300 , 1.5gb RAM, GeForce 6200, 1.2TB HDD between 4 drives so I am pretty sure that's not it. Hopefully i won't happen often. I am going to look into packet shaping or basically putting a cap on samba and ftp so that it doesn't saturate the bandwidth so much.

---

### Post by Spectre5 on 2007-04-22
Hey everyone....you may want to try this:

Change default depth in xorg.conf file from 24 to 16.....I don't know if that has fixed all of my crashes or not, but that Scite crash I described doesn't happen anymore...

Hopefully no more crashes!

-Scott

---

### Post by boyz on 2007-04-23
hii.. I'm a newbie on ubuntu ..and i wanted to install the 3D desktop on it.. So, can anyone plzzz help me and guide me plzz ... I would very appreciate it .. I'm using Pentium M 1.60 and having a Sis M661Mx display card.. So, plz help me, anyone.. ??

---

### Post by boyz on 2007-04-23
hii, i'm a newbie to linux .. So, i dunno how to install the beryl and everything that makes the 3D effect .. So, can anyone help me plzz ... I would really appreciate it .. My laptop are running on sis m661mx graphic card.. So, i hope someone can plz guide me .. Thanx ..

---

### Post by dannyboy79 on 2007-04-23
boyz, this is not the thread to ask that in. please create a new post as no one will answer that in here.

---

