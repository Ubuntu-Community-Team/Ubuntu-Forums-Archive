---
title: "no sound"
date: 2007-01-10
forum: General Help
---

### Post by simonsimon on 2007-01-10
Hi

I have no sound at all.  I'm also pretty sure I've never had sound in Ubuntu.  I'm using Edgy and it is the first distro I've installed.  

Sound works fine in XP.    

I've followed some guides from the forums [here]("http://http://www.ubuntuforums.org/showthread.php?t=334144&highlight=no+sound") and [here]("http://www.ubuntuforums.org/showthread.php?t=205449").

I've also made sure that my settings are correct in alsamixer.

Can anyone help?

Here's some info:

```
simon@laptop:~$ **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
simon@laptop:~$** lspci -v**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d1ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: 52000000-520fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 58
        Memory at d2404000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=0c, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d2000000-d20fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000051f00000
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1880 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 50
        I/O ports at 18c8 [size=8]
        I/O ports at 18ac [size=4]
        I/O ports at 18c0 [size=8]
        I/O ports at 18a8 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d2404400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0398 (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 135b
        Flags: bus master, fast devsel, latency 0, IRQ 185
        Memory at 52000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

08:06.0 CardBus bridge: Texas Instruments Unknown device 8039
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at d2004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 54000000-55fff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

08:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 64, IRQ 233
        Memory at d2007000 (32-bit, non-prefetchable) [size=2K]
        Memory at d2000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

08:06.2 Mass storage controller: Texas Instruments Unknown device 803b
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 64, IRQ 66
        Memory at d2005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

08:06.3 Class 0805: Texas Instruments Unknown device 803c
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 64, IRQ 74
        Memory at d2007800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 66, IRQ 74
        Memory at d2006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>
```

Thanks.

---

### Post by pgilmon on 2007-01-10
I have a HP dv5161 with a HDA sound card. Sound works in ubuntu 6.10, but only if I don't hibernate the computer.

Microphone has never worked for me on this laptop. Seems to me that HDA support in linux is still very limited.

---

### Post by Johnsie on 2007-01-10
Sometimes other distros are better at dealing with different hardware. Choose the distro that suits your hardware best. Maybe you will have more luck with suse or fedora. Also, if this is a problem with Ubuntu make sure you report this on [http://www.launchpad.net](http://www.launchpad.net) to make sure the devs know about it.

---

### Post by simonsimon on 2007-01-10
I can get sound from the CD so I believe I should be able to get sound from this distro.

I'm digging Ubuntu and I'm not ready to leave just yet.

Also I believe others are using the same laptop (HP Pavilion dv8000) without this problem.

Anyone know where I can start troubleshooting?

---

### Post by Johnsie on 2007-01-10
You can ask in the irc too... If you have xchat you should go into that. It's really good sometimes for getting answers fast. Do you have a volume control icon? If so does it have the mute sign on it?

---

### Post by simonsimon on 2007-01-10
I have a volume control icon and it's not muted.  I can open it and see the alsa mixer and both master and PCM are maxed out and not muted.

---

### Post by Johnsie on 2007-01-10
hmmm... usually if Ubuntu can't find a card it's muted and is crossed out with a red circle (like a no-smoking sign).  Some cd's players are directly connected to the sound card and will play without the need for any software. You could try changing your default sound device in System->Preferences or the player you are using to play the sound. I searched around and found these but I dunno if they will help:

[http://www.ubuntuforums.org/showthread.php?t=334777&highlight=no+sound](http://www.ubuntuforums.org/showthread.php?t=334777&highlight=no+sound)
[http://www.ubuntuforums.org/showthread.php?t=208641&highlight=no+sound](http://www.ubuntuforums.org/showthread.php?t=208641&highlight=no+sound)
[http://www.ubuntuforums.org/showthread.php?t=315866&highlight=no+sound](http://www.ubuntuforums.org/showthread.php?t=315866&highlight=no+sound)

I'm no expert so I can't help much more but I hope you find a solution :-)

---

