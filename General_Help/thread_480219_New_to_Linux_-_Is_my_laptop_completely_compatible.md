---
title: "New to Linux - Is my laptop completely compatible?"
date: 2007-06-21
forum: General Help
---

### Post by Alkarl on 2007-06-21
Hi
I'm new to Linux and I have a question
Is my Toshiba Satellite A100 (PSAA9A-118038) compatible with Linux... I can't seem to get it to work properly
If you need any more information... e-mail or PM me

---

### Post by Titus A Duxass on 2007-06-21
> If you need any more information... e-mail or PM me - that's not how it works here.
You post your problems, and we tell you how to fix them.

Have you done a search on the forum?

---

### Post by Alkarl on 2007-06-21
Oh sorry... I didn't know...

I had found some help when searching the forums but I still have problems with Bluetooth, FingerPrint Reader, Some sound problems, my Fn key and my screens resolution (but I know a way to fix this).

My Bluetooth wont send or receive files - or find other devices from the computer
FingerPrint Reader doesn't work at all
Sound isn't very loud
Fn key does nothing except turn on the light for it

The screen resolution can be fixed with the editing of xorg.conf right?

If I can get help with the above problems, I will be very grateful.

Edit: I just found out how to get Bluetooth to work. I think.
Edit2: And I got the Fn key to work... I was searching for the wrong things

---

### Post by jackmc on 2007-06-21
People in [this thread]("http://ubuntuforums.org/showthread.php?t=353847&highlight=fingerprint+reader") have fingerprint readers working, start there maybe :)

And welcome, I hope you get everything sorted out. Bluetooth can be a pain, but its good once it is set up :)

---

### Post by Alkarl on 2007-06-21
Ok thanks... By the looks of it that might work!

Now just the sound problems... anyone got any ideas?
Is there a program designed to boost sound or something?

---

### Post by jackmc on 2007-06-21
I cant help with sound sorry. Not wanting to sound stupid, but have you checked the volume? I dont know any other boosters or anything relating to sound sorry..

---

### Post by Alkarl on 2007-06-21
Yeah... I've checked every sound mixer and setting that I could find... all at 100%

---

### Post by rax_m on 2007-06-21
Hi.. 


The command to check what sound card you have is and can be run from a terminal window :
lspci -v 

Best to run the command and paste the output here as a start. 

There are lots of sound how to's on the forums.. that's probably the best place to start looking though. 

I think that a common fix for the low sound volume issue was to install the latest version of Alsa. 
However, the best thing to do is probably post what make of sound card your laptop has.. 

Disclaimer: I'm no Linux guru.. but I did manage to make sound work on my Toshiba P100 (though with a much more obscure workaround :) )

---

### Post by Alkarl on 2007-06-23
Result of lspci -v

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: cd000000-ceffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [88] Subsystem: Toshiba America Info Systems Unknown device ff10
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f0c00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f0600000-f06fffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff10
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f0700000-f07fffff
        Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff10
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f0800000-f08fffff
        Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff10
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f0c04000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=0b, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f0900000-f09fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff10

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 110M / GeForce Go 7300 (rev a1) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at cd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at ce000000 (64-bit, non-prefetchable) [size=16M]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
        Subsystem: Toshiba America Info Systems PRO/1000 PL
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0600000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 2000 [size=32]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at f0800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at f0906000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=07, secondary=08, subordinate=0b, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 17
        Memory at f0905000 (32-bit, non-prefetchable) [size=2K]
        Memory at f0900000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 18
        Memory at f0904000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 18
        Memory at f0905800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

```

---

### Post by rax_m on 2007-06-23
Seems you have the same type of audio device as me:

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

But since you're already getting sound I suggest upgrading to the latest version of the Alsa drivers.. 

You can follow the advice on this link to do that .. it worked well for me:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The latest version of Alsa is 1.0.14 BTW. Check that yours is an older version before upgrading it (alsamixer -v) in a terminal should give you the version. 

Hope that helps.

---

### Post by Alkarl on 2007-06-23
Thanks! It worked!

---

### Post by rax_m on 2007-06-23
no problem .. glad it worked. 

Good idea to also mark your thread with [solved] at the front of your subject!

---

