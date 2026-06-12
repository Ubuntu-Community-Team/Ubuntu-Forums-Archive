---
title: "Messed up Nvidia driver install, how to revert?"
date: 2013-07-08
forum: General Help
---

### Post by Triblaze on 2013-07-08
Well, I screwed stuff up.

Cliffs: ~~~
-Messed up installing Nvidia propreitary drivers, now Unity doesn't work and the resolution is all screwy, ie drivers not working.
-Need to either fix or revert to Nouveau, which I never uninstalled.
-So far clearest path to me seems removing Nvidia drivers and deleting xorg.conf to let Nouveau take back over.
~~~
Ubuntu 12.10, 64-bit. Dual-booted with Windows 8, not that that matters in this situation.

I attempted to install the Nvidia drivers (propreitary, from here on "nvidia drivers" refers to such, and not nouveau) from the command line. Pretty much, here's the terminal history, if you want to see what I did (I was following some instructions I found online):
 1145  sudo apt-get install build-essential linux-source linux-headers
 [it didn't know which know which headers to install, so I used the following command]
 1147  sudo apt-get install linux-headers-`uname -r`
 1150  sudo apt-get install nvidia-current-updates
 1152  sudo nvidia-xconfig
 [at this point I restarted to find things screwy]
 1154  sudo apt-get install nvidia-current
 1155  sudo nvidia-xconfig

So pretty much, I just tried installing nvidia-current as opposed to nvidia-current-updates, which may be it but probably isn't.

Here's what my computer's current situation is:
It seems that the graphical drivers are not working, as the screen is low res, and 4:3 instead of taking up the full widescreen. Unity seems to be non-existant, there is no launcher, or top panel, my Unity hotkeys do not work either, fortunately ctrl+alt+T works, so I've been able to launch programs from the terminal. I'm posting this from the computer, so it's functional, just void of graphical capabilities and Unity. Currently saving all my files just in case, and considering my options. Firstly, I'm going to restart and hope using nvidia-current instead of nvidia-current-updates fixes it. I expect this to not work, so I'll probably be back here shortly. Hopefully, someone here can offer advice to help me either get the Nvidia drivers working, or revert to the Nouveau drivers, that would be the best option. Other options include fully reinstalling Ubuntu since I have my files stored, or internally upgrading to 13.04 in the hope that it changes to working graphic drivers.

Note: Looking around online, it seems that the "/etc/X11/xorg.conf" file I created for the Nvidia drivers prevents the Nouveau drivers from working. I never uninstalled the Nouveau drivers (may be part of the problem), so maybe I could delete that file (as ArchWiki suggests) and then remove the Nvidia drivers, which will let Nouveau take back over. I assume this will be accomplished by "sudo apt-get purge nvidia-current", or should I use "apt-get remove"? Purge removes config files, which I assume I want.

Going to be restarting soon and will check back here in a bit. Hopefully someone has some insight.

Thanks.

---

### Post by Triblaze on 2013-07-08
Back from restarting, didn't fix, quite predictably. This message popped up both times I started Ubuntu since the driver messup, copied it this time, not sure if this helps:
```
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 1)
Trying modes for CRTC 65
CRTC 65: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 65: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 1)
```

Also, just tried checking "nvidia-settings" in terminal, it tells me:
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
I have run "nvidia-xconfig" as root several times, no change. Going to restart X now.

---

### Post by Frogs Hair on 2013-07-08
Nouveau is default  and installed with the OS . Was there a particular reasons you used the terminal and not software & updates > additional drivers to install nvidia current  ?   With terminal access to applications you could install synaptic and remove and install drivers from there .  ```
sudo apt-get install synaptic 
``````
gksudo synaptic 
```  You can also get into software & updates > additional drivers from Software Center > Edit > Software Sources.

---

### Post by Triblaze on 2013-07-08
Thanks for the reply, I'm trying to remember if this was when I was on 12.04 or if this was on 12.10, but last time I tried using additional drivers it didn't work out too well, so I avoided it this time.

Just checked Synaptic, I found nvidia-current, going to try removing now.
-Should I remove, or completely remove? Just being cautious, don't want to make this any worse. And I assume I should remove "/etc/X11/xorg.conf" as well, provided the removal process doesn't?

---

### Post by efflandt on 2013-07-08
It would have been much simpler to use **Additional Drivers** in **System Settings** to install nvidia drivers. Then you simply **Activate** the driver you want and reboot when that finishes.

Although, when I tried 12.10 (which changed something related to video) I seem to remember having to install the kernel headers first (maybe that was if installed from Software Center). Not sure if you also need the **-generic** headers or if that is just for 64-bit. Maybe you also need **dkms** if that is not installed (for auto upgrading modules with kernel versions). It is easiest to install Synaptic and mark from a list in that what you want to install.

I screwed up my video in 12.04 using apt-get to try to switch back and forth between nvidia-current and nvidia-current-updates (when my actual problem was a failing video card) and ended with bits a pieces of both. I don't think purging packages with apt-get is as easy as installing them because I think you need a more explicit package version. I could not figure out how to fix it, so I gave up and reinstalled Ubuntu. Currently I am using most recent experimental drivers (from Additional Drivers) because that is what Steam recommends. I have an xorg.conf, but it is totally empty (32" 1080p HDTV for monitor):
```
efflandt@xps8100-1204:/etc/X11$ cat xorg.conf

efflandt@xps8100-1204:/etc/X11$ ls -l xorg.conf
-rw-r--r-- 1 root root 1 May  9 13:44 xorg.conf
```What is your video related output from: sudo lspci -v

To see what nvidia related things are installed now try: dpkg-query -l nvidia*

Maybe someone can help you purge things back to a sane state.

Also if your computer and monitor have DVI or HDMI (a simple adapter cable can connect DVI to HDMI) that might more reliably pick a correct native resolution. VGA usually just comes up with a generic list that might or might not have what you want.

---

### Post by Triblaze on 2013-07-08
sudo lspci -v:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d2000000-d2ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: [88] Subsystem: Lenovo Device 3977
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Capabilities: [d94] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d3000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at d3700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d3714000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d3719000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d3710000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d3600000-d36fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3977
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: d3500000-d35fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3977
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: d3400000-d34fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3977
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d3718000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 3977
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at d3717000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: medium devsel
    Memory at d3715000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd4 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

02:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)
    Subsystem: Lenovo Device 3979
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d3600000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable- Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-27-78-da-20-89-84-ff
    Kernel driver in use: alx
    Kernel modules: alx

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d3500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 9c-4e-36-ff-ff-90-ca-20
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
    Subsystem: Lenovo Device 3976
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d3403000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30) (prog-if 01)
    Subsystem: Lenovo Device 3976
    Flags: fast devsel, IRQ 19
    Memory at d3402000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel modules: sdhci-pci

04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
    Subsystem: Lenovo Device 3976
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d3401000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)
    Subsystem: Lenovo Device 3976
    Flags: bus master, fast devsel, latency 0
    Memory at d3400000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-


```

dpkg-query -l nvidia*:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  nvidia-173     <none>                    (no description available)
un  nvidia-173-upd <none>                    (no description available)
un  nvidia-180-mod <none>                    (no description available)
un  nvidia-185-mod <none>                    (no description available)
un  nvidia-96      <none>                    (no description available)
un  nvidia-96-upda <none>                    (no description available)
un  nvidia-common  <none>                    (no description available)
ii  nvidia-current 304.88-0ubun amd64        NVIDIA binary Xorg driver, kernel
un  nvidia-current <none>                    (no description available)
un  nvidia-current <none>                    (no description available)
rc  nvidia-current 304.88-0ubun amd64        NVIDIA binary Xorg driver, kernel
un  nvidia-experim <none>                    (no description available)
un  nvidia-setting <none>                    (no description available)
un  nvidia-setting <none>                    (no description available)
un  nvidia-setting <none>                    (no description available)
ii  nvidia-setting 304.88-0ubun amd64        Tool for configuring the NVIDIA g


```

If/When I get this fixed, I'll try additional drivers, but I seem to recall that not working. Maybe didn't have the kernel headers. Will try installing -generic now, I don't think I have those, which could be it seeing as I'm on 64-bit.
I have dkms.

-Btw, just checked and Additional Drivers is empty, nothing there. Not sure what that means.

---

### Post by efflandt on 2013-07-08
I am not familiar with newer computers that have both integrated Intel video and other video, but someone more familiar with that may know if you also need bumblebee [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Triblaze on 2013-07-08
> **efflandt said:**
> I am not familiar with newer computers that have both integrated Intel video and other video, but someone more familiar with that may know if you also need bumblebee [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I'm not too familiar with the inner workings of them either, but I don't think it should matter much, seeing as everything's been working fine up until now.

Anyway, right now I'm trying to decide between using synaptic to remove nvidia-current, or installing the newest experimental drivers via synaptic. I assume installing the newest will automatically remove nvidia-current? I also installed headers-generic, which may very well fix it when I install the drivers, but I'm not sure.

-Just installed experimental drivers, restarting and crossing fingers now. If this fails I'll try removing everything.
--Nothing, still the same, going to try removing nvidia propreitary stuff and seeing if it works.

---

### Post by Triblaze on 2013-07-08
Great news! Everything's back to normal!
I don't know what caused the problems, but it seems the drivers did not agree with my system for some reason.
Whenever installing, the console usually had some debug problem about not recognizing the system, or quirck, or something. Might have been it.

Anyway, I just removed all the nvidia propreitary stuff via synaptic, and got rid of the xorg.conf files, and restarted to find it working with the nouveau drivers again. I guess a pretty straightforward solution, but unfortunately I couldn't get the propreitary drivers working.

I'll leave this thread open for another hour in case anyone has any suggestions for getting them working or anything, but for now I think I'm fine as is, and I'll close this thread as solved in about an hour.

---

