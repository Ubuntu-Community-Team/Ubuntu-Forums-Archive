---
title: "82801I (ICH9 Family) doesn't produce sound."
date: 2008-01-07
forum: General Help
---

### Post by akuzura on 2008-01-07
This is a very weird problem i'm getting.. First of all I want to point out that I am very new to ubuntu, and to the whole linux scheme. When I installed Ubuntu, the first thing I wanted to do was to make beryl work. The sound was working at this point. Having heard of beryl, I instantly googled "beryl on ubuntu" and followed the instructions for edgy eft, thinking it would probably be the same for Gruesome Goblin. I started doing some small updates (something similar to sudo apt-get upgrade and update, etc)
Afterwards, I gave up and PMed my linux friend who instructed me to do tons of sh!t, and in the end my sound isn't working anymore.
I followed the instructions to the guy who has a fix for the intel built in soundcards (almost mine, H8 family) thinking this would work, but no (I didn't complete the fatal last step)
Now I'm out of ideas.
Help me out ya'll

---

### Post by balaknair on 2008-01-07
Could you please open a terminal and type 
aplay -l
lspci -v
and copy paste the output here. It'll help anyone who wants to help get a better idea. If you were to post a link to the "instructions to the guy who has a fix for the intel built in soundcards" that would help too. 

I also did a search of alsa-project.org and other Linux forums. ALSA supports the ICH9 cards since version 1.0.14. The problem could be  with the kernel you're using(the hda-intel module has problems with modified kernels, better to use the generic kernel-that might be one of the things that got changed when you did apt-get upgrades).

So if you could just post the info, I'm sure a solution can be found.

---

### Post by akuzura on 2008-01-08
lspci -v
> 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8276
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f4000000-f7dfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at b800 [size=32]
        Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at b880 [size=32]
        Capabilities: <access denied>

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at bc00 [size=32]
        Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f3fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 829f
        Flags: bus master, fast devsel, latency 0, IRQ 15
        Memory at f3ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Prefetchable memory behind bridge: 00000000f2f00000-00000000f2ffffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f7f00000-f7ffffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: f7e00000-f7efffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at b080 [size=32]
        Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at b400 [size=32]
        Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at b480 [size=32]
        Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at f3fff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f8000000-febfffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
        I/O ports at a000 [size=8]
        I/O ports at 9c00 [size=4]
        I/O ports at 9880 [size=8]
        I/O ports at 9800 [size=4]
        I/O ports at 9480 [size=16]
        I/O ports at 9400 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: medium devsel, IRQ 5
        Memory at f3fff400 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0400 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
        I/O ports at b000 [size=8]
        I/O ports at ac00 [size=4]
        I/O ports at a880 [size=8]
        I/O ports at a800 [size=4]
        I/O ports at a480 [size=16]
        I/O ports at a400 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0420
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at cc00 [size=128]
        [virtual] Expansion ROM at f7de0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8226
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f7ec0000 (64-bit, non-prefetchable) [size=256K]
        Expansion ROM at f7ea0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 824f
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f7ffe000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at f7fe0000 [disabled] [size=64K]
        Capabilities: <access denied>

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 824f
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at dc00 [size=8]
        I/O ports at d880 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=16]
        Capabilities: <access denied>

05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Unknown device 0031
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at ec00 [size=32]
        Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at fe9ff800 (32-bit, non-prefetchable) [size=2K]
        I/O ports at e880 [size=128]
        Capabilities: <access denied>

aplay -l
> aplay: device_list:204: no soundcards found...


---

### Post by balaknair on 2008-01-08
The Creative X-fi card isn't supported by ALSA at present as far as I know, but the ICH9 should work once ALSA is configured.
OK looks like you've run nto the same issue I had earlier when I upgraded 7.04 to 7.10
I think it could be something to do with the kernel(ALSA snd-hda-intel module works fine with the linux generic kernel but apparently has issues with customised kernels- the sound card isn't even detected).
I ended up doing a clean install of Gutsy(my partition got corrupted when I tried to fix something else) and didn't have much trouble after that.

Anyway, I think you could try purging ALSA and reinstalling it from scratch
In a terminal
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

This will remove ALSA. To reinstall it,
sudo apt-get install linux-sound-base alsa-base alsa-utils

Just copy and paste(& enter password when prompted to do so)
Reboot

Then try aplay -l again. If the sound card is detected, in terminal
cat /proc/asound/card0/codec#* | grep Codec

This will give you the model your card is. 
Go to this page [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)
and check the entries for your model.
eg:on my PC I got "Codec: Analog Devices AD1986A"

and in ALSA-configuration.txt(the link above) I found
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)

Select the description which matches your setup(eg. a 5.1 surround with 6 output channels will be 6stack)

Then go to the terminal
sudo nano /etc/modprobe.d/alsa-base

This will open a file in the terminal, use down arrow key to go to the end of the file and add this line at the end
options snd-hda-intel model=MODEL

replace MODEL with the model from the ALSA-Configuration.txt that you found earlier
eg. options snd-hda-intel model=6stack

save and exit
reboot

Upon rebooting you ought to have sound.

If on the other hand after purging and reinstalling ALSA your card is still not detected, you might have to revert to the generic linux kernel. Instructions on how to do that are available in the forum, but we'll deal with that when we get to that point.

Wishing you luck

---

