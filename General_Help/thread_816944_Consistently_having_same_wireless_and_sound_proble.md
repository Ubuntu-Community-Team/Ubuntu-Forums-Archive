---
title: "Consistently having same wireless and sound problem"
date: 2008-06-03
forum: General Help
---

### Post by FOBoi1122 on 2008-06-03
Hi guys, 

I've reinstalled ubuntu multiple times, and i've always had the same problem. When running ubuntu, I will sometimes need to restart the computer. If i get unlucky, both my wireless and sound disappear. I've tried to uninstall all the things i installed to check and see if that would maybe cancel the error but there's no luck there.

when i type iwconfig, i get this:
lo        no wireless extensions.

eth0      no wireless extensions.

Also, if i load a different kernel (8.10 the -16 recovery one), I get sound and wireless. (not sure if will still). But all the other ones i've tried to load get no sound or wireless. So my question is, is there a way to copy the good kernel over to the other ones? or someway repair this? it's getting really annoying and i'm considering just switching back to xp or vista because i can't figure this out.

Thanks for your help in advance.

---

### Post by FOBoi1122 on 2008-06-03
bump anyone?

---

### Post by danwood76 on 2008-06-03
The recovery mode uses the same kernel as the standard mode, it just loads up in single user mode.

I would have thought it would be an issue with the wireless or sound module your machine uses.

What sound card and graphics card do you have?
could you post the output of the following command in the terminal please:
```

lspci -v

```

---

### Post by FOBoi1122 on 2008-06-03
Hi, i'm currenting using the generic recovery kernel, and everything's working fine, but here's the output:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Fujitsu Limited. Unknown device 13f2
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Fujitsu Limited. Unknown device 13f9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Fujitsu Limited. Unknown device 13f9
	Flags: bus master, fast devsel, latency 0
	Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Limited. Unknown device 1414
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Limited. Unknown device 1414
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Fujitsu Limited. Unknown device 1415
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fc704800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Fujitsu Limited. Unknown device 142d
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fc200000-fc2fffff
	Prefetchable memory behind bridge: 00000000c4000000-00000000c40fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0f, sec-latency=0
	Memory behind bridge: fc300000-fc3fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Limited. Unknown device 1414
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Limited. Unknown device 1414
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Limited. Unknown device 1414
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Fujitsu Limited. Unknown device 1415
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fc704c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1c, subordinate=24, sec-latency=32
	Memory behind bridge: fc400000-fc4fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Fujitsu Limited. Unknown device 140e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Fujitsu Limited. Unknown device 140f
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Fujitsu Limited. Unknown device 1411
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 221
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fc704000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Fujitsu Limited. Unknown device 1413
	Flags: medium devsel, IRQ 11
	Memory at c4100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
	Subsystem: Fujitsu Limited. Unknown device 139a
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	[virtual] Expansion ROM at c4000000 [disabled] [size=128K]
	Capabilities: <access denied>

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1100
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at fc300000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

1c:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
	Subsystem: Fujitsu Limited. Unknown device 143d
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 18
	Memory at fc402000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=1c, secondary=1d, subordinate=20, sec-latency=176
	Memory window 0: c8000000-cbfff000 (prefetchable)
	Memory window 1: cc000000-cffff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00003000-000030ff
	16-bit legacy interface ports at 0001

1c:03.1 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
	Subsystem: Fujitsu Limited. Unknown device 143d
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 18
	Memory at fc403000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=1c, secondary=21, subordinate=24, sec-latency=176
	Memory window 0: d0000000-d3fff000 (prefetchable)
	Memory window 1: d4000000-d7fff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001

1c:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Fujitsu Limited. Unknown device 143d
	Flags: bus master, slow devsel, latency 32, IRQ 18
	Memory at fc401000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

1c:03.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Fujitsu Limited. Unknown device 143d
	Flags: slow devsel, IRQ 11
	Memory at fc400000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

---

### Post by danwood76 on 2008-06-03
Well your sound card is well supported by alsa, it _should_ work fine.

Boot up normally so you have wifi and sound non working and enter the following commands into the terminal, they will try to load the modules that are the drivers for the two parts.

```

sudo modprobe iwl4965 # This loads the wifi drivers
sudo modprobe snd_hda_intel # This loads the alsa drivers

```
If neither throw out errors then the modules are loading correclty.

---

### Post by FOBoi1122 on 2008-06-03
bad news, they won't load =[ 
so here's the output when i did it.


jay@jay-laptop:~$ sudo sudo modprobe iwl4965
FATAL: Module iwl4965 not found.
jay@jay-laptop:~$ sudo sudo modprobe snd_hda_intel
FATAL: Module snd_hda_intel not found.

also, i read somewhere that the wireles and the sound may be in conflict because they're sharing the same ports or something?

---

### Post by danwood76 on 2008-06-03
I doubt it, you dont need to do sudo sudo btw.

If they say not found it means they arent built for your current kernel.
Which kernel version are you using?
If its a custom kernel I would bet that you didnt enable the intel drivers when you recompiled, you also need to compile alsa after building a custom kernel.

The intel drivers are part of the default kernel and the alsa is part of the default package.

---

### Post by FOBoi1122 on 2008-06-03
Hi danwood, 
First i'd just like to say i really appreciate you helping me with this. It's really been bothering me.

The kernel version i'm using is 2.64.24-17-386 as well as 2.64.24-17-generic. they both won't load the sound and wireless. Could you please elaborate a little on how to compile the sound and intel drivers? I'm not sure if i made a custom kernel since I've always just let it boot up whichever kernel is on top, which is the 2.64.24-17-386 kernel unless i did something funky and made it a custom kernel.

---

### Post by danwood76 on 2008-06-03
A custom kernel involves recompiling so you would know if you had done it.
Odd thing about the modules though, they should be installed.

There is a package in the repos that looks like the modules check you have it installed by running this command:
```

sudo apt-get install linux-ubuntu-modules-2.6.24-17-generic

```

---

### Post by FOBoi1122 on 2008-06-03
Yup, it's been installed.

sudo apt-get install linux-ubuntu-modules-2.6.24-17-generic
[sudo] password for jay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-ubuntu-modules-2.6.24-17-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

