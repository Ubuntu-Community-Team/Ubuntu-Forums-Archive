---
title: "Ubuntu 16.04 audio drivers Lenovo L570"
date: 2018-03-13
forum: General Help
---

### Post by Drenriza on 2018-03-13
I have installed the Ubuntu 16.04 server distribution on my Lenovo L570 laptop, to get
a minimal installation for my i3 environment.

Now i would like to install the audio drivers for the laptop and i am considering how this can be done.
```
sudo aplay -l
```
> 
card 0: PCH [HDA Intel PCH], device 0: ALC293 Analog [ALC293 Analog]
device 3: HDMI 0
device 7: HDMI 1
device 8: HDMI 2


On the Ubuntu wiki upgrading ALSA [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
it says that you need is to install DKMS
```
sudo apt-get install dkms
```

Than go to this page [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)
and download the correct package for my system and install with dpkg -i [package], reboot.

As far as i can tell this will install the audio drivers for my system?? I would than like to install MOC with ffmpeg plugin to be able to listen to .mp3 files.
Would this be the correct way to go about this or is their another better way?

Seeking advice.

Thanks in advance
Best regards

---

### Post by T.J. on 2018-03-13
I'd think that you would not need to do that.  Most Intel devices are supported by default.  I'm not trying to tell you what to do, but I'd investigate further before I'd resort to using a snapshot, as the code is inherently unstable. Unless you are a developer, it could make a really big mess.  Using unstable code has the potential to crash your system, and you could lose data.  Almost as bad, if it does not install properly, you could damage your installation database and then have to reinstall the entire operating system. 

Could you post your hardware list from an "lspci -vnn" please?

---

### Post by Drenriza on 2018-03-14
Thanks for the reply T.J.
So as i understand you even though i have installed the server edition the audio drivers should be supported per default?

The output of lspci is as follows.
```

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:5904] (rev 02)
    Subsystem: Lenovo Device [17aa:2249]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:5916] (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:2249]
    Flags: bus master, fast devsel, latency 0, IRQ 137
    Memory at f0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915_bpo
    Kernel modules: i915_bpo

00:08.0 System peripheral [0880]: Intel Corporation Sky Lake Gaussian Mixture Model [8086:1911]
    Subsystem: Lenovo Skylake Gaussian Mixture Model [17aa:2249]
    Flags: fast devsel, IRQ 255
    Memory at f274a000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>

00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21) (prog-if 30 [XHCI])
    Subsystem: Lenovo Sunrise Point-LP USB 3.0 xHCI Controller [17aa:2249]
    Flags: bus master, medium devsel, latency 0, IRQ 126
    Memory at f2720000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP Thermal subsystem [17aa:2249]
    Flags: fast devsel, IRQ 255
    Memory at f274b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI [8086:9d3a] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP CSME HECI [17aa:2249]
    Flags: bus master, fast devsel, latency 0, IRQ 138
    Memory at f274c000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Sunrise Point-LP SATA Controller [AHCI mode] [17aa:2249]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 127
    Memory at f2748000 (32-bit, non-prefetchable) [size=8K]
    Memory at f274f000 (32-bit, non-prefetchable) [size=256]
    I/O ports at e080 [size=8]
    I/O ports at e088 [size=4]
    I/O ports at e060 [size=32]
    Memory at f274d000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:9d10] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 120
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation Device [8086:9d13] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 121
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f2600000-f26fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port [8086:9d14] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: f2500000-f25fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:9d18] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.2 PCI bridge [0604]: Intel Corporation Device [8086:9d1a] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f1b00000-f24fffff
    Prefetchable memory behind bridge: 00000000f1000000-00000000f19fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.3 PCI bridge [0604]: Intel Corporation Device [8086:9d1b] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 125
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: f1a00000-f1afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d58] (rev 21)
    Subsystem: Lenovo Device [17aa:2249]
    Flags: bus master, medium devsel, latency 0

00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP PMC [17aa:2249]
    Flags: fast devsel
    Memory at f2744000 (32-bit, non-prefetchable) [disabled] [size=16K]

00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d71] (rev 21)
    Subsystem: Lenovo Device [17aa:2249]
    Flags: bus master, fast devsel, latency 64, IRQ 139
    Memory at f2740000 (64-bit, non-prefetchable) [size=16K]
    Memory at f2730000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP SMBus [17aa:2249]
    Flags: medium devsel, IRQ 255
    Memory at f274e000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at efa0 [disabled] [size=32]
    Kernel modules: i2c_i801

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-V [8086:15d8] (rev 21)
    Subsystem: Lenovo Ethernet Connection (4) I219-V [17aa:2249]
    Flags: bus master, fast devsel, latency 0, IRQ 129
    Memory at f2700000 (32-bit, non-prefetchable) [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

03:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:1010]
    Flags: fast devsel, IRQ 255
    Memory at f2600000 (64-bit, non-prefetchable) [disabled] [size=8K]
    Capabilities: <access denied>

04:00.0 Non-Volatile memory controller [0108]: Intel Corporation Device [8086:f1a5] (rev 03) (prog-if 02 [NVM Express])
    Subsystem: Intel Corporation Device [8086:390a]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: nvme
    Kernel modules: nvme

07:00.0 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8621] (rev 01) (prog-if 01)
    Subsystem: Lenovo Device [17aa:2249]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f1a01000 (32-bit, non-prefetchable) [size=4K]
    Memory at f1a00000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci

```

---

### Post by T.J. on 2018-03-14
```



00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d71] (rev 21)
    Subsystem: Lenovo Device [17aa:2249]
    Flags: bus master, fast devsel, latency 64, IRQ 139
    Memory at f2740000 (64-bit, non-prefetchable) [size=16K]
    Memory at f2730000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel




```

According to this the device is already detected and the driver loaded.  We just need to see if it is correctly set up, and then decide what to do.  I'll have to check the specs on your laptop.  Is that the exact model number: L570?

> So as i understand you even though i have installed the server edition the audio drivers should be supported per default?



Unlike Windows, there is no material difference between server and desktop Linux other than what is installed by default.  Your confusion is quite understandable.  You can easily convert one to the other or be somewhere inbetween.

---

### Post by Drenriza on 2018-03-14
How does one check if it's correctly setup?

> Is that the exact model number: L570?
Yeb

---

### Post by T.J. on 2018-03-15
So in the meantime...I installed Ubuntu on a disk this morning.  I have a Realtek sound chip similar to yours.  Not the same, but similar.  I noticed that the sound is muted by default on a new install.  Have you checked that yet?

---

### Post by Yellow Pasque on 2018-03-16
> **Drenriza said:**
> even though i have installed the server edition the audio drivers should be supported per default?

Yes. They are part of the kernel.

> How does one check if it's correctly setup?

Try to play a sound. Use aplay or moc, or whatever you'd like. There's even a program called speaker-test: [https://linux.die.net/man/1/speaker-test](https://linux.die.net/man/1/speaker-test)
NOTE: Make sure volume is moderated in 'alsamixer' if you are in a public environment.

---

### Post by Drenriza on 2018-03-19
Thanks guys! As you said it all worked when i just opened moc and started to play some music.
Though i dont quite understand since audio does not work on for example youtube.com where i first tested.

But i got my initial problem solved which was my local audio files.

---

### Post by T.J. on 2018-03-20
Please mark the thread as solved if you are satisfied.

---

