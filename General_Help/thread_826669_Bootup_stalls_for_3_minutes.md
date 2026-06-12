---
title: "Bootup stalls for 3 minutes"
date: 2008-06-12
forum: General Help
---

### Post by Pete89 on 2008-06-12
Hello,

I have a recent install of Xubuntu 8.04 on my Thinkpad x31 working just fine. There is just one problem:

During bootup the splash screen appears and the status bar lights up going from right to left and visa versa. Then the status bar begins to load the OS and lights from left to right. When its gets about a tenth of the way across it just stops there for three minutes. Syslog starts up at that moment too, so there is nothing in the logs telling me what is going on.


Any ideas??

---

### Post by prshah on 2008-06-12
> **Pete89 said:**
>  Then the status bar begins to load the OS and lights from left to right. When its gets about a tenth of the way across it just stops there for three minutes.

a) When the status bar shows up, Press Ctrl+Alt+F8 to switch to the output terminal which will show loading messages. When you switch, it may be blank, but it will start filling up with messages within a few minutes.

--OR--

b) When in grub, select the entry you want to boot; DONT press enter. Press "E" to edit the line, then, from the end of one of the lines, remove the word "splash". Press enter, then press "b" to boot into your selected ubuntu.

Now you should get a bunch of messages on the screen instead of the splash screen. If you see anything suspicious, post back here for more info/solutions/workarounds.

---

### Post by Pete89 on 2008-06-12
OK I got rid of the splash screen. Here is the error message:

Loading hardware driver:
219.682461 intel-rng: FWH NOT detected

And there it stays for three minutes and then boots up normally.

Thanks,

P.

---

### Post by prshah on 2008-06-12
> **Pete89 said:**
> 
Loading hardware driver:
219.682461 intel-rng: FWH NOT detected


This message is normal, it simply means that you don't have required hardware support (FirmWare Hub) for a Random Number Generator (rng); I get it on both my intel desktop and laptop. 

I think your delay is caused by what follows this message; in my case, it's the PCI hotplug driver (which I think controls OS-based PnP).```

dmesg | grep -i -A 3 -B 3 rng
[   47.165902] agpgart: Detected an Intel 855GM Chipset.
[   47.166413] agpgart: Detected 8060K stolen memory.
[   47.225932] agpgart: AGP aperture is 128M @ 0xd8000000
[   47.263438] intel_rng: FWH not detected
[   47.311463] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.467399] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.615205] iTCO_vendor_support: vendor-support=0

```

Are you using any PCMCIA cards? Can you eject them before bootup and see if delay still occurs?

Do you have a BIOS option for PnP? If so, can you toggle it and check if the delay still persists?

---

### Post by Pete89 on 2008-06-12
Not using  any PCMCIA cards and I was not able to find the Plug and PLay option in the bios. Here is the dmesg output:

[   27.755527] Linux agpgart interface v0.102
[   27.807516] agpgart: Detected an Intel 855PM Chipset.
[   27.821579] agpgart: AGP aperture is 256M @ 0xd0000000
[   27.911312] intel_rng: FWH not detected
[   28.420150] input: Power Button (FF) as /devices/virtual/input/input2
[   28.434821] ACPI: Power Button (FF) [PWRF]
[   28.434957] input: Lid Switch as /devices/virtual/input/input3

Thanks for your help.. I do appreciate it very much!

---

### Post by prshah on 2008-06-13
> **Pete89 said:**
> Not using  any PCMCIA cards and I was not able to find the Plug and PLay option in the bios. Here is the dmesg output:

[   27.821579] agpgart: AGP aperture is 256M @ 0xd0000000



(Grasping at straws)

My AGP aperture setting is 128M, do you think that can make a difference?

Do you have any swap set up?

---

### Post by Pete89 on 2008-06-13
> **prshah said:**
> (Grasping at straws)

My AGP aperture setting is 128M, do you think that can make a difference?

Do you have any swap set up?

yeah I have a 1gb of swap space. How could I go about changing the AGP aperture ...?

---

### Post by Pete89 on 2008-06-13
I found this:

[http://ibm-acpi.sourceforge.net/](http://ibm-acpi.sourceforge.net/)

Which has some files like this:

ibm-acpi-0.13-20070310_v2.6.20.2.patch.gz

But nowere do they explain what you have to do with these files .....

---

### Post by prshah on 2008-06-14
> **Pete89 said:**
> yeah I have a 1gb of swap space. How could I go about changing the AGP aperture ...?

You can change it in the BIOS, the setting will be called "AGP Aperture Size".

Note that I don;t know what this does, I'm just making a blind guess, I'd say you're on the right track with the IBM ACPI thingy.

---

### Post by spiderbatdad on 2008-06-14
I have to boot my thinkpad with the lapic pci=routeirq options on the kernel line in /boot/grub/menu.lst with --quiet splash removed.

dmesg will give you a diagnostic message from the kernel during the boot process. It will tell you if you need to run some options...like lapic or acpi=off...

```
dmesg > ~/Desktop/dmesg.txt
```

---

