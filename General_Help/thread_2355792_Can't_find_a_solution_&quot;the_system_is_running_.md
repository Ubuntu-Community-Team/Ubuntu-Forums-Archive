---
title: "Can't find a solution &quot;the system is running in low graphics mode&quot; ubuntu 16.04"
date: 2017-03-16
forum: General Help
---

### Post by hunterloh92 on 2017-03-16
I was trying to install a graphics driver and I must have installed the wrong one, after I install the driver and rebooted this is the message i get. "The system is running in low graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself." I have tried other solution of these forums but nothing has worked. I'm new to ubuntu (have to learn for a new job) so any solutions are welcome, but please keep them as simple as possible.

Using ubuntu 16.04, computer is an hp envy 14 about 6 years old

Thank you.

---

### Post by Bashing-om on 2017-03-16
hunterloh92l Hi ! Welcome to the forum .

We need to know the hardware to know what the correct driver is.
Post back - Between code tags - the outputs of terminal commands:
```

lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

We see what it takes
[INDENT][INDENT]to make all right
[/INDENT][/INDENT]

---

### Post by hunterloh92 on 2017-03-16
Output for code 1:
00:02.0 VGA compatible controller: Intel corporation 2nd genegeration Core Processor Family Integrated Graphics Controller (rev 09) Subsystem: Hewlett-Packard Company 2nd generation Core Processor Family Integrated Graphics Controller
Kernel driver in use :i915

01:00.0 VGA compatible controller: advanced micro devices, Inc.  [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] (rev ff) 
DeviceName: ATI Whistler
Kernel driver in use: radeon 


Output for code 2:
*-display
Description: VGA compatible controller 
Product: 2nd Generation Core Processor Family Integrated Graphics Controller
Vendor: Intel Corporation 
Physical id: 2
Bus info: pci@0000:00:02.0
Version: 09
Width: 64 bits 
Clock: 33MHz
Capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
Resources: irq:33 memory:c8000000-c83fffff memory:b0000000-bfffffff ioport:4000(size=64)



Sorry if the formatting is weird, I'm doing this all on my phone.

Thank you for your help, and let me know what else you need from me.

---

### Post by Bashing-om on 2017-03-16
hunterloh92

Ouch! hybrid graphics;  Intel/AMD
Tell more about :
> 
I was trying to install a graphics driver and I must have installed the wrong one

which driver, for which graphic's set from where ?

Be aware in 16.04 there are no other drivers than are offered in the kernel for the AMD card.
What is installed for FGLRX at this time ?
Post:
```

dpkg -l | grep fglrx 

```

making all all right ->
[INDENT][INDENT]might be a real trial
[/INDENT][/INDENT]

---

### Post by hunterloh92 on 2017-03-16
Output for code:
ii boinc-client-fglrx        7.6.31+dfsg-6ubuntu1        amd64   metapackage for AMD/ATI fglrx-savvy BOINC client and manager 

ii fglrx-pxpress     1:0.4.17.2      amd64    transitional package for ubuntu-drivers-common


Thanks again

---

### Post by Bashing-om on 2017-03-16
hunterloh92; Regrets

I do not know enough about the boinc-client to offer an opinion here .

But still we are in the dark as to " which driver, for which graphic's set from where ? " .

[INDENT][INDENT]a know-it-all ---- I am not
[/INDENT][/INDENT]

---

### Post by hunterloh92 on 2017-03-16
I'm not 100% sure as to which driver or set, I was on the AMD website if I can remember correctly.

---

