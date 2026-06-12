---
title: "No audio"
date: 2007-08-02
forum: General Help
---

### Post by superbungalow on 2007-08-02
I can play videos and sounds fine, but they just don't make a noise. There a re no errors when trying to play sounds they just don't come out of my laptop speakers.

---

### Post by renzokuken on 2007-08-02
could you post the output of ```
lspci -v
``` and your laptop barand + model
it should give us some info about your particular audio chipset

---

### Post by superbungalow on 2007-08-02
Yup:

```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
	Subsystem: Unknown device 1631:c101
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0000000-d00fffff
	Prefetchable memory behind bridge: d8000000-dfffffff
	Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Unknown device 1631:c101
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at d0407000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 20000000 [disabled] [size=512K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Unknown device 1631:c101
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d0404000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Unknown device 1631:c101
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d0405000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Unknown device 1631:c101
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d0406000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
	Subsystem: Unknown device 1631:c101
	Flags: 66MHz, medium devsel
	I/O ports at 8040 [size=16]
	Memory at d0407400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device 1631:c101
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
	Subsystem: Unknown device 1631:c101
	Flags: bus master, slow devsel, latency 64, IRQ 18
	Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Unknown device 1631:c101
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=0e, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
	Subsystem: Unknown device 1631:c101
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0020000 [disabled] [size=128K]
	Capabilities: <access denied>

09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Unknown device 1631:c101
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at a000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

My computer is a packard bell easynote. Thanks a lot!

---

### Post by renzokuken on 2007-08-02
i think updating/compiling the latest alsa-driver should fix it.

assuming you have a working net connection run the following commands

```

sudo apt-get install build-essential
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar xjf alsa-driver-1.0.14.tar.bz2
cd alsa*
./configure
make
sudo make install

```

then **reboot** and see if it works. you may have to run

```
alsamixer
``` and set the volume levels

good luck

---

### Post by superbungalow on 2007-08-02
thanks, I'll do that now, also, what is alsa?

---

### Post by renzokuken on 2007-08-02
its the Advanced Linux Sound Architecture.....i think of it as a sound driver that works for almost all chipsets

the homepage explains it better than i can

[http://www.alsa-project.org/](http://www.alsa-project.org/)

each release supports a whole host of new hardware and so the current version (1.0.14) may support your hardware which the defualt ubuntu version (1.0.12) doesnt

---

### Post by superbungalow on 2007-08-02
oh, I get it, thanks, also, the update worked, thanks a lot, I finally get get to hear the ubuntu logon sound! :)

---

### Post by neoroses on 2007-09-25
thank you so much this is the only bloody post that actuly works, it eventualy gives me sound!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! thank you

---

### Post by renzokuken on 2007-10-01
glad it worked for you too neoroses

---

### Post by neoroses on 2007-10-02
any way of getting the head phone jack to work aswelll mate?

---

### Post by renzokuken on 2007-10-03
sorry man, no idea.......head p-hone seems to be a problem with alot of audio chipsets.......

my advice would be to keep updating alsa each time a new version is released till they get it working.....the one you installed above was alsa-driver 1.0.14 and i'm pretty sure 1.0.15 is available (in RC or Beta at least)

---

### Post by neoroses on 2007-10-03
ok thanks is there a way of wgeting alsa 1.0.15? also is it worth trying the alsa plugings?
thanks mate your a great help

---

### Post by renzokuken on 2007-10-03
you can either get it direct from their website [www.alsa-project.org](www.alsa-project.org) (top right of home page ..... 1.0.15 is at rc3 stage so should be pretty stable)

or use

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
```

the plugins may help yes and would be worth a try but not sure how successful

---

### Post by neoroses on 2007-10-05
thanks mate your a top help

---

