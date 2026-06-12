---
title: "Yet another no sound thread- worked 3 days ago not yesterday"
date: 2008-04-24
forum: General Help
---

### Post by wormeyman on 2008-04-24
So i updated to hardy last thrusday and my audio only worked in flash.  Disabling my intel onboard audio chip in the bios solved the problem and it worked system wide on my audigy 2 now it is no longer working again at all even in flash.  I thought the speakers might be the problem but when i plug the speaker cord in to my mp3 player it sounds just fine.

---

### Post by twright on 2008-04-24
goto /system/preferences/sessions and add a new entry with killall pulseaudio as the command

---

### Post by wormeyman on 2008-04-24
I tried that and i was asked to re-configure alsa which i did:
> eric@ubuntu:~$ asoundconf list
Names of available sound cards:
Audigy
eric@ubuntu:~$ asoundconf set-default-card Audigy
eric@ubuntu:~$ 



---

### Post by wormeyman on 2008-04-24
bump it's still not working :(

---

### Post by jhnphm on 2008-04-25
Install libflashsupport and undo what twilight said


There's no reason to kill PA if you set things up right.

---

### Post by wormeyman on 2008-04-25
I'll do that but even system sounds aren't working right now so i'm pretty sure that something is misconfigured for the whole sound card.

---

### Post by twright on 2008-04-25
for now sound seems to be unstable with pulseaudio enabled, this will change with testing but for now it seems to break stuff> **jhnphm said:**
> Install libflashsupport and undo what twilight said


There's no reason to kill PA if you set things up right.

---

### Post by wormeyman on 2008-04-27
so i'm back from a weekend away and my problem has yet to be resolved i'm thinking that something might have been misconfigured?  When i installed the RC it worked and then a few days later and a lot of mb in patches it stopped working?

---

### Post by wormeyman on 2008-04-28
Hope this helps someone:

> eric@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
	Flags: bus master, fast devsel, latency 0
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: fa900000-fe9fffff
	Prefetchable memory behind bridge: d2600000-f26fffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ec00 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: f2700000-f27fffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Unknown device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Subsystem: Gateway 2000 Unknown device 5288
	Flags: medium devsel, IRQ 5
	I/O ports at e000 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Gateway 2000 Unknown device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e400 [size=256]
	I/O ports at e080 [size=64]
	Memory at febffc00 (32-bit, non-prefetchable) [size=512]
	Memory at febff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>

02:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs SB0090 Audigy Player/OEM
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>

02:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
	Subsystem: Creative Labs SB Audigy FireWire Port
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)
	Subsystem: Gateway 2000 Unknown device 5288
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d880 [size=64]
	Capabilities: <access denied>


---

### Post by wormeyman on 2008-04-28
so does anyone have any ideas?

---

### Post by wormeyman on 2008-04-30
So yeah i'm still having problems...

---

### Post by twright on 2008-04-30
in /system/preferences/sound select alsa for everything

---

### Post by wormeyman on 2008-04-30
thanks for the tip but still no luck

---

### Post by twright on 2008-05-01
could you post the outcome of the command pulseaudio?

---

