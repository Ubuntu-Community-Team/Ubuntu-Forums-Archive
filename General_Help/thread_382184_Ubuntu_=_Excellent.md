---
title: "Ubuntu = Excellent"
date: 2007-03-11
forum: General Help
---

### Post by Eminem on 2007-03-11
Well, I just got Ubuntu to work and so far I'm satisfied with it. The only problem, however is the fact that I can't play mp3 files **[COLOR="Red"]and[/COLOR]** because I cannot make my screen resolution higher than 1024 by 768 in **System > Preferences > Screen Resolution** when my monitor should display 1280 by 1024. Any help with this will be greatly appreciated.

---

### Post by aliyanage on 2007-03-11
try installing the 915resolution package

```
sudo apt-get install 915resolution
```

it worked for me hope it does for you, let me know...


regards
aliyanage

---

### Post by llamakc on 2007-03-11
> **Eminem said:**
> Well, I just got Ubuntu to work and so far I'm satisfied with it. The only problem, however is the fact that I can't play mp3 files **[COLOR=Red]and[/COLOR]** because I cannot make my screen resolution higher than 1024 by 768 in **System > Preferences > Screen Resolution** when my monitor should display 1280 by 1024. Any help with this will be greatly appreciated.


Please, please use better titles for threads. 

Googling for your problem(s) and you may have found this:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)  [for mp3's]

Do you know what video card you have? Run this in the Terminal and cut-n-paste it here.

```

lspci -v

```

---

### Post by aliyanage on 2007-03-11
sorry I forgot after installing the 915resolution restart and have a look at what resolutions are available...

regards
aliyanage

---

### Post by Eminem on 2007-03-11
This is what I got:
> 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
        Subsystem: Dell Unknown device 0160
        Flags: bus master, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
        Subsystem: Dell Unknown device 0160
        Flags: fast devsel, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at feb80000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0160
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0160
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0160
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at ff40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0160
        Flags: bus master, medium devsel, latency 0, IRQ 201
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe900000-feafffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 0160
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at ffa0 [size=16]
        Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: Dell Unknown device 0160
        Flags: medium devsel, IRQ 3
        I/O ports at eda0 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 0160
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
        Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:04.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA])
        Subsystem: VISIONTEK Unknown device 0280
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 185
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at de00 [size=256]
        Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fe900000 [disabled] [size=128K]
        Capabilities: <access denied>

01:05.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02) (prog-if 00 [Generic])
        Subsystem: Dell Unknown device 0001
        Flags: bus master, fast devsel, latency 64, IRQ 169
        Memory at fe9ed000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ddf0 [size=16]
        Capabilities: <access denied>

01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Dell Unknown device 8127
        Flags: bus master, fast devsel, latency 64, IRQ 169
        Memory at fe9ee000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at fe920000 [disabled] [size=16K]
        Capabilities: <access denied>


---

### Post by llamakc on 2007-03-11
Does the OP have an Intel graphics chipset? If not, how is that package going to be helpful?

---

### Post by Eminem on 2007-03-11
> **llamakc said:**
> 
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)  [for mp3's]


The problem with that is that I get lost with this:
> ...and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.

I don't know where "Add" is and I see no "check boxes".

---

### Post by llamakc on 2007-03-11
That page doesn't reflect the current version of Synaptic in Edgy.

There's no "add". From the first tab titled "Ubuntu 6.10", you want to click the checkboxes for "universe, multiverse". I have all of them checked.

After that, close the window, and hit RELOAD in Synaptic. Next, search for those packages and install them. 

Another way is to open a Terminal and cut/paste this:

```

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

---

