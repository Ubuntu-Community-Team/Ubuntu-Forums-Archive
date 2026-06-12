---
title: "Feisty Freezes a lot!!"
date: 2007-06-26
forum: General Help
---

### Post by rem on 2007-06-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/122322](https://bugs.launchpad.net/ubuntu/+bug/122322) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

I know there are a lot of  "system freezers" out there but I thought to post a new one explaining my own experience (Also filed bug #122322 on LaunchPad with the same issue).

The system freezing problem is happening more often and it's getting very annoying with Feisty Fawn.
The freezing seems to happen randomly and first, the mouse pointer can be moved, then few areas of the screen becomes unclikable, then the right click button is disabled, then the mouse and the entire system is freezing. After hard reboot, sometimes Grub is not starting and it's requiring few more hard reboots until able to start Feisty again. Sometimes, even after few hard reboots Feisty isn't starting at all only after 30min / 1 hr break (PC turned OFF). Happened when watching movies, using Firefox, Nautilus, Jedit, Audacious and / or other actions I can't even be aware of or reproduce. 

Same problem with the nVidia driver ON or OFF.
System is updated up to this day.

Feisty was fresh installed on PC with specs as follows:

SYSTEM INFORMATION
	Running Ubuntu Linux, the 4.0 release.
	GNOME: 2.18.1 (Ubuntu 2007-04-10)
	Kernel version: 2.6.20-16-generic (#2 SMP Thu Jun 7 20:19:32 UTC 2007)
	GCC: 4.1.2 (i486-linux-gnu)
	Xorg: 7.2.0 (04 April 2007)
	Hostname: rem
	Uptime: 0 days 0 h 14 min

CPU INFORMATION
	AuthenticAMD, AMD Sempron(tm) 2500+
	Number of CPUs: 1
	CPU clock currently at 1749.838 MHz with 256 KB cache
	Numbering: family(6) model(8) stepping(1)
	Bogomips: 3501.62
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts

MEMORY INFORMATION
	Total memory: 757 MB
	Total swap: 3482 MB

STORAGE INFORMATION
	Primary Master /dev/hda - disk
		Model: MAXTOR STM3250820A
		Capacity: 244.2 GB
		Cache: 8.192 MB
	Primary Master /dev/hdb - cdrom
		Model: HL-DT-ST DVDRAM GSA-4167B
		Capacity: no media

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Silicon Integrated Systems [SiS] 746 Host (rev 10)
	PCI bridge(s)
		Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
	USB controller(s)
		Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
		Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
		Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	ISA bridge
		Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
	IDE interface
		Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])

GRAPHIC CARD
	VGA controller
		nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2) (prog-if 00 [VGA])

SOUND CARD
	Multimedia controller
		Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
		Subsystem: Elitegroup Computer Systems Unknown device 1808

NETWORK
	Ethernet controller
		Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
		Subsystem: Realtek Semiconductor Co., Ltd. RT8139

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce4 MX 440 with AGP8X
	Card Type: AGP 8x
	Video RAM: 64 MB
	GPU Frequency: 274 MHz
	Driver version: NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006

Thank you!

---

### Post by pickarooney on 2007-06-28
Sounds quite similar to my problem, if it's any consolation.

---

### Post by rem on 2007-06-28
There might be a fix for this (at least for me it worked, because I kept an eye on it and I didn't had a crush in the past 2 days). I think there might be a problem with Feisty and poor cooling of CPU. I teared my PC apart and cleaned every bit of it (fans, radiators, ram, etc ...) 

I remember a few years ago when I was a Windows user I had a similar problem when Windows kept rebooting by itself until I had my PC parts cleaned. Feisty (or other OSs) might just act differently but because of the same problem ... Same stuff was somehow confirmed by Sitsofe Wheeler (thank you) on [**this**]("https://bugs.launchpad.net/ubuntu/+bug/122322") launchpad bug post by showing me [**this**]("http://people.redhat.com/davej/hardware-problems.txt") check list and very interesting, the cooling problem is addressed right on top of it.

Don't wanna act smart and tell you this is it...  just shared what I experienced.

Good luck.

---

### Post by pickarooney on 2007-06-29
I don't think this is it. Maybe it's crappy nvidia drivers again. Does anyone know how to install the 1.0.9746 nVidia drivers via Envy? These ones worked OK for me and I think upgrading to Feisty installed bugy drivers.

---

### Post by Crafty Kisses on 2007-06-29
> **rem said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/122322](https://bugs.launchpad.net/ubuntu/+bug/122322) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

I know there are a lot of  "system freezers" out there but I thought to post a new one explaining my own experience (Also filed bug #122322 on LaunchPad with the same issue).

The system freezing problem is happening more often and it's getting very annoying with Feisty Fawn.
The freezing seems to happen randomly and first, the mouse pointer can be moved, then few areas of the screen becomes unclikable, then the right click button is disabled, then the mouse and the entire system is freezing. After hard reboot, sometimes Grub is not starting and it's requiring few more hard reboots until able to start Feisty again. Sometimes, even after few hard reboots Feisty isn't starting at all only after 30min / 1 hr break (PC turned OFF). Happened when watching movies, using Firefox, Nautilus, Jedit, Audacious and / or other actions I can't even be aware of or reproduce. 

Same problem with the nVidia driver ON or OFF.
System is updated up to this day.

Feisty was fresh installed on PC with specs as follows:

SYSTEM INFORMATION
	Running Ubuntu Linux, the 4.0 release.
	GNOME: 2.18.1 (Ubuntu 2007-04-10)
	Kernel version: 2.6.20-16-generic (#2 SMP Thu Jun 7 20:19:32 UTC 2007)
	GCC: 4.1.2 (i486-linux-gnu)
	Xorg: 7.2.0 (04 April 2007)
	Hostname: rem
	Uptime: 0 days 0 h 14 min

CPU INFORMATION
	AuthenticAMD, AMD Sempron(tm) 2500+
	Number of CPUs: 1
	CPU clock currently at 1749.838 MHz with 256 KB cache
	Numbering: family(6) model(8) stepping(1)
	Bogomips: 3501.62
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts

MEMORY INFORMATION
	Total memory: 757 MB
	Total swap: 3482 MB

STORAGE INFORMATION
	Primary Master /dev/hda - disk
		Model: MAXTOR STM3250820A
		Capacity: 244.2 GB
		Cache: 8.192 MB
	Primary Master /dev/hdb - cdrom
		Model: HL-DT-ST DVDRAM GSA-4167B
		Capacity: no media

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Silicon Integrated Systems [SiS] 746 Host (rev 10)
	PCI bridge(s)
		Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
	USB controller(s)
		Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
		Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
		Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	ISA bridge
		Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
	IDE interface
		Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])

GRAPHIC CARD
	VGA controller
		nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2) (prog-if 00 [VGA])

SOUND CARD
	Multimedia controller
		Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
		Subsystem: Elitegroup Computer Systems Unknown device 1808

NETWORK
	Ethernet controller
		Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
		Subsystem: Realtek Semiconductor Co., Ltd. RT8139

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce4 MX 440 with AGP8X
	Card Type: AGP 8x
	Video RAM: 64 MB
	GPU Frequency: 274 MHz
	Driver version: NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006

Thank you!
It could be a possible resource issue.

---

### Post by rem on 2007-07-02
I have just installed the CPU sensors and the "Computer Temperature Monitor" and xsensors applet. The temperatures reported are M/B 42.0 Celsius Degrees, CPU temp. is constantly up to 127 Celsius Degrees and a third temperature (which I don't know what is) 63.0 degrees. I can't properly interpret this data since I'm not a hardware expert but even so My guess is that 127 Celsius might be a bit higher than normal. What should I do in this case? Please help ...

I just saw that temperatures of 127 deg and respectively 63 deg are the 2nd and 3rd thermal zones (I'm completely lost). The 1st thermal zone is up to 43 which seems to be the right one. I'm just guessing though... can you advice please? 

Thanks!

---

### Post by john8791 on 2007-07-17
Mine freezes exactly like you described.  The mouse pointer still moves but I can't kill the X server with ctl-alt-bckspce or open a vterm with ctl-alt-F1.  I have a motherboard with the SiS chipset and use the on board Sis video card.  I sure hope someone figures this out.

BTW, Is there a recommended hardware list for Ubuntu?  If not there should be.

Thanks

---

### Post by rem on 2007-07-17
> **john8791 said:**
> Mine freezes exactly like you described.  The mouse pointer still moves but I can't kill the X server with ctl-alt-bckspce or open a vterm with ctl-alt-F1.  I have a motherboard with the SiS chipset and use the on board Sis video card.  I sure hope someone figures this out.

BTW, Is there a recommended hardware list for Ubuntu?  If not there should be.

Thanks

Just to let you know ..

There's one thing I did and it looks like it was a hardware conflict. A friend of mine suggested to switch both HDD and DVD jumpers on cable select and set them on BIOS to be automatically recognized. I had the HDD set on master and the DVD on slave. After the jumper switch operation Feisty runs smoother and it doesn't freeze anymore.

---

### Post by regomodo on 2007-07-17
> **rem said:**
> I have just installed the CPU sensors and the "Computer Temperature Monitor" and xsensors applet. The temperatures reported are M/B 42.0 Celsius Degrees, CPU temp. is constantly up to 127 Celsius Degrees and a third temperature (which I don't know what is) 63.0 degrees. I can't properly interpret this data since I'm not a hardware expert but even so My guess is that 127 Celsius might be a bit higher than normal. What should I do in this case? Please help ...

I just saw that temperatures of 127 deg and respectively 63 deg are the 2nd and 3rd thermal zones (I'm completely lost). The 1st thermal zone is up to 43 which seems to be the right one. I'm just guessing though... can you advice please? 

Thanks!

127 Celsius?! Jesus, that's a hot CPU!

---

### Post by rem on 2007-07-17
> 127 Celsius?! Jesus, that's a hot CPU!

I'm not very experienced with this kind of hardware testing procedures but  can tell now that the 1st temperature was the exact heat report after all ... I did try to use it and make some pancakes though but it didn't worked so the 127 degrees temperature for sure wasn't the right one ...  ;)

---

### Post by david_2001 on 2007-07-17
> **rem said:**
> I'm not very experienced with this kind of hardware testing procedures but  can tell now that the 1st temperature was the exact heat report after all ... I did try to use it and make some pancakes though but it didn't worked so the 127 degrees temperature for sure wasn't the right one ...  ;)

Your PC is almost the exact specification of my last PC with the only real difference being that I had a Sempron 3100+ cpu.  Anyway, assuming that you have lm-sensors set up properly - did you run sensors-detect? - even 42C is hot.  Mine hardly ever went over 32C and this was in a small, tightly-packed case with not very efficient cooling.  If 127C is anywhere near a real temperature for any component (cpu, video card, whatever) then it's going to be a good candidate cause of the creeping system paralysis.

---

