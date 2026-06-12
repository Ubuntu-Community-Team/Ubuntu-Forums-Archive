---
title: "Problem with Multi-Monitor Support over Dedicated Graphics Card AND Onboard Graphics"
date: 2016-10-29
forum: General Help
---

### Post by aki-to on 2016-10-29
I was looking quite a while on the internet for a solution to this problem, but obviously didn't find much help that could've helped me in my special situation. I got a third monitor yesterday, so I tried to plug it in my computer, but my graphics card, called GeForce GTX970, has only 2 DVI and one HDMI input. I already use both DVI inputs and my third monitor is only VGA compatible. So I plugged it into my mainboard, but I can't really do anything with it in Linux. Neither can I set it up as extended display, nor as duplicate. At least the monitor is turned on and working, as it shows an underscore on a blackscreen and the monitor's menu is accessible, as well.

Now comes the part, that I researched already: Yes, my BIOS is perfectly configured to support a multi-monitor setup in this way. Yes, it even works on Windows 10 **flawlessly** without any problems whatsoever. So obviously, the problem lies within the Linux operating system. Windows just uses the onboard graphics drivers as well as the graphics card's ones simultaneously without any issues.

So my question is now: how can I get this set-up to work?

Also please don't ask or point at the HDMI input. No. Even if there might be a solution by plugging in all monitors in the graphics card I still want to have a solution that works for using the onboard and dedicated graphics simultaneously in Linux.

That said, I would appreciate your help, thank you.

Monitor Specs:

1. ASUS VN289 @60Hz FullHD (1920x1080)

2. SAMTRON @70Hz 1280x1024

3. HP 1940 @60Hz 1280x1024

---

### Post by T.J. on 2016-10-30
Most of the time, hardware is detected and configured automatically.

X11 was probably only configured to use the discrete card.  If you are using the commercial driver, the installer provided by Nvidia did that to you. - not Linux specifically. Most of the commercial drivers automatically assume that they are the only card present.  AMD does that too, and yes - it IS very annoying, but easily mended.  I realize that must seem strange to you as a Windows user, but a lot of the time, the companies simply give you the driver and expect you to know how to use it.   In the world outside of Windows you have to occasionally get your hands dirty - but it is worth it.  Especially when it comes to having flexibility or actual privacy, IMO - something Windows 10 does not offer.

I can't help you enable the on-board card until you tell me what it is.  Please run the "lspci -vnn" command in a terminal and post its output here.  The diagnostic tool will tell me what kind of equipment you have.  After that, we can hopefully have enough information to reconfigure the X11 GUI to meet your needs.

---

### Post by aki-to on 2016-10-30
I appreciate your valuable contribution. It kind of hit me reading that I am accused of being a Windows user.  :biggrin::biggrin::biggrin: I am certainly not an IT-professional (yet, since I'm still a student), but I wouldn't describe myself as a Windows user anyway, because I just use it mainly because of games. So the point is, that I understand fully what you are saying and that the "getting hands dirty" part is certainly not an unkown planet for me. Also I expected the problem originating from the Nvidia driver, when I remembered that I specifically changed the driver to the newest Beta version.

lspci -vnn output:

```
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)	Subsystem: ASUSTeK Computer Inc. 4th Gen Core Processor DRAM Controller [1043:8534]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: hsw_uncore


00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 26
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f6000000-f70fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:02.0 Display controller [0380]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
	DeviceName:  Onboard IGD
	Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [1043:8534]
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915


00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
	Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [1043:8534]
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at f7834000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


00:14.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB xHCI Controller [8086:8cb1] (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family USB xHCI Controller [1043:8534]
	Flags: bus master, medium devsel, latency 0, IRQ 29
	Memory at f7820000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci


00:16.0 Communication controller [0780]: Intel Corporation 9 Series Chipset Family ME Interface #1 [8086:8cba]
	Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family ME Interface [1043:8534]
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Memory at f783e000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei_me
	Kernel modules: mei_me


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
	DeviceName:  Onboard LAN
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I218-V [1043:85c4]
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at f7800000 (32-bit, non-prefetchable) [size=128K]
	Memory at f783c000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e


00:1a.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2 [8086:8cad] (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family USB EHCI Controller [1043:8534]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at f783b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci
	Kernel modules: ehci_pci


00:1b.0 Audio device [0403]: Intel Corporation 9 Series Chipset Family HD Audio Controller [8086:8ca0]
	Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family HD Audio Controller [1043:8602]
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at f7830000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


00:1d.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1 [8086:8ca6] (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family USB EHCI Controller [1043:8534]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f783a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci
	Kernel modules: ehci_pci


00:1f.0 ISA bridge [0601]: Intel Corporation 9 Series Chipset Family Z97 LPC Controller [8086:8cc4]
	Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family Z97 LPC Controller [1043:8534]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich


00:1f.2 SATA controller [0106]: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode] [8086:8c82] (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family SATA Controller [AHCI Mode] [1043:8534]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 30
	I/O ports at f0d0 [size=8]
	I/O ports at f0c0 [size=4]
	I/O ports at f0b0 [size=8]
	I/O ports at f0a0 [size=4]
	I/O ports at f060 [size=32]
	Memory at f7839000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci


00:1f.3 SMBus [0c05]: Intel Corporation 9 Series Chipset Family SMBus Controller [8086:8ca2]
	Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family SMBus Controller [1043:8534]
	Flags: medium devsel
	Memory at f7838000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f040 [size=32]
	Kernel modules: i2c_i801


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM204 [GeForce GTX 970] [10de:13c2] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. GM204 [GeForce GTX 970] [1043:8508]
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at f7000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia


01:00.1 Audio device [0403]: NVIDIA Corporation GM204 High Definition Audio Controller [10de:0fbb] (rev a1)
	Subsystem: ASUSTeK Computer Inc. GM204 High Definition Audio Controller [1043:8508]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel



```

Thank you for helping.

---

### Post by T.J. on 2016-10-30
> I appreciate your valuable contribution. It kind of hit me reading that I am accused of being a Windows user. 



Not at all.  It was merely a statement of fact.  My only interest is assisting you with your problem.  What I said was meant to reassure you that I understand your situation. It was not offered as a criticism.  I've worked with all of the major players &#8211; Linux, Windows and Mac over the last 20+ years and they ALL have their problems.  While I admit, I have a strong distaste for Windows (in particular for the design and ethical problems that it represents), you are welcome to use whatever you want.  I won't pass judgment.

I have a smilar situation in that I have an Nvidia and AMD card in the same machine.  The commercial driver installer disables other cards until you enable them manually.  I should warn you, however, that if you use the commercial driver, Nvidia replaces the OpenGL libraries with ones that are incompatible with display chips made by other makers.  We can make it work, but it is likely that you will have 2D/Xvideo but no OpenGL ability on the third monitor.   Blame Nvidia for not building on top of the standard Mesa OpenGL that comes with Linux.   If you are using the open driver - Nouveau - this is not an issue and we can use the same OpenGL for all chips.  On the other hand, Nouveau is not as fast as Nvidia's driver - so there is a trade-off.    The only other way around it is to program your installation for two copies of X11 running in parallel; and Ubuntu does not support that as far as I know.  

There may be another way that I am not aware of - I am not omniscient.

 > 
 
  I just use it mainly because of games. 

So do I, in a KVM.

> 
So the point is, that I understand fully what you are saying and that the "getting hands dirty" part is certainly not an unkown planet for me. Also I expected the problem originating from the Nvidia driver, when I remembered that I specifically changed the driver to the newest Beta version.

 
Good.  Your willingness to work the problem is appreciated. If I might say so, your positive attitude will take you far.


 
 ```

 
 00:02.0 Display controller [0380]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
     DeviceName:  Onboard IGD
     Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [1043:8534]
     Flags: bus master, fast devsel, latency 0, IRQ 28
     Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
     Memory at d0000000 (64-bit, prefetchable) [size=256M]
     I/O ports at f000 [size=64]
     Capabilities: <access denied>
     Kernel driver in use: i915
     Kernel modules: i915

``` 
 
 
So your on-board card is an Intel and it is already recognized.  The driver is loaded so the only concern is configuring your /etc/X11/xorg.conf to turn on the display.  This part will be trial and error.  I don't use Intel hardware but I should be able to get you going in the right direction.  

Will you please post your xorg.conf file?  If you have them, please include any relevant details, such as the model of your display and how it is connected - so that we can fine-tune it for best performance.

---

### Post by aki-to on 2016-10-30
After I found out that I don't have an xorg.conf, I was searching the internet a lot and tried many possible solutions for making an own xorg.conf, as well as making additional configurations in "/etc/X11/xorg.conf.d". None of them seemed to work. So I guess, let's do it the slow but persistent and detailled way.

Here is the output of -

My *20-nvidia.conf*:

```
Section "Device"    Identifier "Device0"
    Driver     "nvidia"
    VendorName "NVIDIA Corporation"
    Option     "NoLogo" "True"
EndSection
```

What I found closest to, what I imagine is, the potential solution of my problem, was information describing how to use two graphics card in a Linux environment by making an additional "Device" section in the xorg.conf (or another .conf in ../xorg.conf.d/), which path was defined by setting the PCI input as a BusID, so the program knows which component I try to address by letting it know where it is attached to. Sadly this solution obviously doesn't work for integrated graphics units, as it seems. Maybe there is a different way of setting this "path"?

---

### Post by T.J. on 2016-10-31
You need to generate the first template file with Nvidia's tool. It is named nvidia-xconfig or something similar.  .

---

### Post by aki-to on 2016-10-31
I ran

```
sudo nvidia-xconfig
```

and got this out of the xorg.conf afterwards:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig# nvidia-xconfig:  version 352.79  (buildd@debian)  Wed Apr 27 14:07:29 UTC 2016


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 340.93  (buildd@debian)  


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "STN SAMTRON"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 970"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-4"
    Option         "metamodes" "DVI-I-0: nvidia-auto-select +0+0, DVI-D-0: nvidia-auto-select +1296+7"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by T.J. on 2016-10-31
That helps immensely.  I have to get to work - but will catch up with you soon.

---

### Post by aki-to on 2016-10-31
I wonder if it actually helps that immensely, since that is the output for my graphics card only and doesn't say anything about my third monitor (I think), since it is connected to the Intel HD graphics...

---

