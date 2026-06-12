---
title: "Recompiled the Kernel. Lost WiFi and Sound :("
date: 2008-05-04
forum: General Help
---

### Post by linuxd00 on 2008-05-04
Hi,

using this easy guide:
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

i recompiled the Kernel activating PentiumM optimizations. I removed some other small things as well
[LIST]
[*]Dell Laptop Support, Sony Laptop Support (i have a Thinkpad)
[*] activated Thinkpad ACPI which seemed to be only as a loadable module
[*] since i have an ATI GraCa i removed support fo Nvidia, Trident and that bunch of drivers that come bundled
[/LIST]


after compilation i booted into my new Kernel and while it seems a bit faster it lacks Wifi and Sound (at least i noticed that... maybe more is missing?)
I still seem to have networking but for cable only. and te sound mixer says it cant find a sound device.

in the Restricted drivers manager there are no drivers listed. There used to be the Atheros Wifi driver in there.


So my question:

did i maybe messed up somethin while reconfiguring the kernel? i hope not since as i understood it i just changed the configuration that was used in my current kernel.(and i dont remember deactivating anything about soundcards)

or do i have to load those drivers somehow manually.
Since my nre kernel has a new name.. do i have to copy some drivers to the profile of the new kernel?
I did copy the firmware to /lib/firmware/[mykernel] as stated in the comments of that page. but it seems that isnt it.

i recompiled it twice and now i would like to try out the ZenKernel.. but instead of compiling for another 2 hours and do trial and error i thought i'd ask here.

thanks for answers!

---

### Post by spupy on 2008-05-04
I have a Atheros card, too. You have to reinstall the atheros wifi drivers, since at their install their are build for the running kernel. You compiled a new one and it can't use the drivers you already have installed. 

About the sound issue: What is your sound card?

---

### Post by linuxd00 on 2008-05-04
hi,
thanks for the reply.

My PC is a Thinkpad X31
[http://www.thinkwiki.org/wiki/Category:X31](http://www.thinkwiki.org/wiki/Category:X31)
 lspci says this:
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
(...)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)


```
So from the thinkwikipage:
"On systems where lspci shows an Intel AC'97 Audio Controller, this chip is supported by the snd-intel8x0 kernel module. "

i found the file:
/lib/modules/2.6.24-17-386/ubuntu/sound/alsa-driver/pci/snd-intel8x0.ko

but there is a 
 /lib/modules/2.6.24.3-custom/
directory which is the path of my Kernel... but it doesnt have a "ubuntu" subdirectory on it. just "source", "kernel" and "build".
or can i activate this module directly in the kernel configuration before compiling?


how can i install the atheros driver? will it be built at install.  isnt is closed source?(since it appears in the restricted drivers window)
and where do activate it?

im excited about this :) i hope theres more answers soon!

p.s. just thinking about it... can i do something like ".configure" on the kernel sources so that it recognizes my hardware and which modules to activate? that'd be rad!
im a total newbie to kernels... sorry if this is bugging

---

### Post by spupy on 2008-05-04
> **linuxd00 said:**
> 
So from the thinkwikipage:
"On systems where lspci shows an Intel AC'97 Audio Controller, this chip is supported by the snd-intel8x0 kernel module. "

i found the file:
/lib/modules/2.6.24-17-386/ubuntu/sound/alsa-driver/pci/snd-intel8x0.ko

but there is a 
 /lib/modules/2.6.24.3-custom/
directory which is the path of my Kernel... but it doesnt have a "ubuntu" subdirectory on it. just "source", "kernel" and "build".
or can i activate this module directly in the kernel configuration before compiling?


how can i install the atheros driver? will it be built at install.  isnt is closed source?(since it appears in the restricted drivers window)
and where do activate it?

About the Atheros card: look in Synaptic. I don't have Ubuntu right now, but on Gentoo I'm using the madwifi drivers. They are open source and work well. But I have to reinstall (recompile) them for each new kernel. I have no idea why Ubuntu uses a restricted driver for Atheros, i didn't even know there was one.
**EDIT:** The drivers are indeed open source, but they use proprietary thing.

For sound now. Yes, you have to select the correct module for your sound card before you compile the kernel. Are you using menuconfig? Anyway, first try selecting all drivers for intel sound cards. 
By the way, are you using Ubuntu sources, or downloaded kernel sources from kernel.org? It is possible that the ubuntu sources have some extra patches in them, which could be missing in the main kernel.org sources.

**EDIT:**
Found where the module snd-intel-8x0 is located:
Device Drivers -> Sound -> Advance Linux Sound Arch. -> PCI Devices ->  "Intel/SiS/nVidia/AMD/ALi AC97 Controller"

---

### Post by linuxd00 on 2008-05-04
thanks! 
Wireless worked! 

i downloaded the source from the madwifi page and compiled and activated it using their easy instructions and i got wifi working without reboot.

Actually there is a package which contains the madwifi driver on synaptic... but the sources from the page were easy enough so i didnt bother trying to activate the synaptic package (restricted modules-something)

i'll now recompile the kernel with the sound driver as you said.



i still have to see if its worth and it really is faster that way...
The precompiled Zen-Kernel works with sound and wifi but feels actually slower :(
thanks anyway!

---

### Post by spupy on 2008-05-04
> **linuxd00 said:**
> thanks! 
Wireless worked! 
i still have to see if its worth and it really is faster that way...
The precompiled Zen-Kernel works with sound and wifi but feels actually slower :(
thanks anyway!

Glad to hear it is working! :D
I've never heard of this Zen kernel, but nothing is stopping you from trying. Please report back on how it compares to the kernel you compiled yourself. ;)

Just make sure you always have a backup kernel that 100% works, albeit slowly.

---

### Post by linuxd00 on 2008-05-04
from 
[https://wiki.ubuntu.com/ZenKernel](https://wiki.ubuntu.com/ZenKernel)
> The Zen Kernel is a specialized bleeding edge kernel taken from Linus' git tree, with several patches to increase stability, performance, and compatibility applied.
The Zen Kernel incorporates the Completely Fair Scheduler (CFS), numerous hardware drivers that save you from needing a restricted modules package, many fixes are also included that allow HP laptop users to run without noapic and nolapic in many cases, Madwifi and Intel Wireless drivers ARE included, as well as the b43 wireless driver, among many others. This kernel is faster than the default Ubuntu kernel, and smaller in many ways as well, with an image size of around 1.8mb at the most.



I still have to find a nice benchmarking suite.

I did a quick benchmark of Compiz... which of course depends solely on the GPU and my custom Kernel was slightly slower than the ZenKernel which in turn was slightly slower than the Vanilla Kernel.(3~4FPS in average)
I didnt notice any remarkable differences in RAM usage at start.

so ill try some CPU Benches and post here. stil have to compile the sound working custom kernel

---

### Post by spupy on 2008-05-04
I "benchmark" my kernels by how fast they boot. A custom kernel wont affect RAM usage, i think. It wont make programs that **much** faster. But when the OS is booting, at first it is only the kernel that is working, then you can see how fast it is. The "default" gentoo kernel boots in 10-15 seconds (that is only the kernel, not the whole OS). After i compiled a custom kernel, it boots in 5s...

---

