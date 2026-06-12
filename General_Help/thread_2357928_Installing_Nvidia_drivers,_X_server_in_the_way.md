---
title: "Installing Nvidia drivers, X server in the way"
date: 2017-04-07
forum: General Help
---

### Post by george772 on 2017-04-07
I have the same Problem [as in thread [https://ubuntuforums.org/showthread.php?t=2339529]](https://ubuntuforums.org/showthread.php?t=2339529]) with my Lenovo P40, NVIDIA Quadro M500M.
There are no options under Additional Drivers for the graphic card. I need to install the [COLOR=#545454][FONT=arial]proprietary[/FONT][/COLOR] nvidia driver to have support of OpenGL4, so I can't work with the nouveau driver... the nvidia page says, the graphic card is supported for the linux driver.

```

sudo lspci -vnn :

00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 520 [8086:1916] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Lenovo HD Graphics 520 [17aa:505a]
    Flags: bus master, fast devsel, latency 0, IRQ 279
    Memory at d2000000 (64-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] #1b
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] #13
    Kernel driver in use: i915
    Kernel modules: i915
....


06:00.0 3D controller [0302]: NVIDIA Corporation GM108GLM [Quadro K620M / Quadro M500M] [10de:137a] (rev a2)
    Subsystem: Lenovo Quadro M500M [17aa:505a]
    Flags: bus master, fast devsel, latency 0, IRQ 278
    Memory at d3000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

```


> sudo ubuntu-drivers list :
intel-microcode


Any idea how to get the additional drivers to install proprietary nvidia drivers?

thx

---

### Post by Futant on 2017-04-07
[SIZE=2]Have you added the repository?

```
sudo add-apt-repository ppa:graphics-drivers/ppa

sudo apt update
```

After this you should see some options in Additional Drivers.[/SIZE]

---

### Post by mattseaton on 2017-04-17
That ppa did nothing for me.  I also have the yoga p40.  I installed arch and the card was recognized immediately, so it doesn't look like a driver issue, but an ubuntu issue.  That's an option if you really need it, but for me after suffering through that install I don't even want to bother with arch anymore so I went back to ubuntu gnome where things just work, mostly... except for the graphics card.  Support was supposed to have been added to the nvidia drivers a while back now.  Not sure what's going on.  Hope it gets fixed soon.

---

### Post by Yellow Pasque on 2017-04-17
First off, do not try and install drivers downloaded directly from Nvidia.

> There are no options under Additional Drivers for the graphic card.
Sometimes, the card you have is newer than the database the Additional Drivers utility uses. You could also be seeing this bug:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1492873](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1492873)
No big deal.. You can just install through the terminal (or even use synaptic). Something like this:
```
sudo apt-get install nvidia-375
```
^Seeing as how this is a hybrid graphics system, you probably also need to mess with nvidia-prime, but I'm not the one to ask about that.

---

### Post by george772 on 2017-04-19
thx, but neither the ppa nor the fix from the linked bug helped.
And I already tried to install it manually, but then no graphics worked.

---

### Post by nfm on 2017-04-20
Try giving Fedora 25 a shot, they had done some great work with support for laptops with hybrid graphics.

---

