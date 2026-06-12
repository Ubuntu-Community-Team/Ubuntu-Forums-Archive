---
title: "Wattman AMD &amp; Ubuntu issue"
date: 2016-12-04
forum: General Help
---

### Post by gabers2004 on 2016-12-04
I've had this weird glitch with my dual boot system. When booting ubuntu the screen is locked at 1024x768, when I run 1600x900. I thought this was a problem with xorg.. that I can find, currently no.

I found a fix but it's quite annoying. I have to boot into my windows partition, and it says something about wattman restoring to default settings- I don't know how that fixes it~ but it does.
Anyone know a way to fix it without having to boot into windows? Thanks.

---

### Post by cariboo on 2016-12-05
Please let us know what hardware you are using, especially the graphics adaptor and what driver you are using:

```
sudo lshw -C display
```

should look something like this:

```
sudo lshw -C display
[sudo] password for cariboo: 
  *-display                 
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:90 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8) memory:c0000-dffff
```

---

### Post by gabers2004 on 2016-12-05
Results:

```
gabe@gabe-LinuxBoss:~$ sudo lshw -C display
[sudo] password for gabe: 
  *-display                 
       description: VGA compatible controller
       product: Curacao XT / Trinidad XT [Radeon R7 370 / R9 270X/370X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:30 memory:d0000000-dfffffff memory:fea00000-fea3ffff ioport:e000(size=256) memory:c0000-dffff
gabe@gabe-LinuxBoss:~$
```

---

### Post by QIII on 2016-12-05
Hello!  Please use code tags when posting terminal output.  

You may do so in one of three ways:

1.  Click the # button in the top row of buttons above the text entry box.  Place your cursor between the code tags that appear and type or paste your text.

2.  Type or paste your text, highlight it and click the # button in the top row of buttons above the text entry box.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.



Some questions:  

What is Wattman?  (I know, others who do not use Windows may not)
What release of Ubuntu are you using?
What happens if, after getting the display straight in Ubuntu, you reboot and boot back in to Ubuntu?

What are the results of 

```
lsmod | grep radeon
```

and

```
lsmod | grep amdgpu
```

---

