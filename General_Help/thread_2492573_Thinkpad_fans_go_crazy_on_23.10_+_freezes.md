---
title: "Thinkpad fans go crazy on 23.10 + freezes"
date: 2023-11-15
forum: General Help
---

### Post by simonsaysthis on 2023-11-15
I  have a ThinkPad T14 Gen 3 with Intel i5 1235u. Ubuntu 23.10 is the  distro I really want to use but its also the only distro where the CPU  fan goes in overdrive from the time it boots.

I even have the issue that the welcome app freezes on first boot.


Using 22.04.3 and 23.04 are ok.


First  I thought it must be an issue with the Kernel but strangely enough  Fedora with the same Kernel, namely 6.5, doesn’t suffer from this CPU  fan issue.


I have no idea what it could be. Been searching the internet for similar reports but didn’t find anything.


Anyone here with an Alder Lake laptop that can share their experiences?

---

### Post by #&amp;thj^% on 2023-11-15
The only way I could make one work, was with the OEM install and a OEM kernel.
Note: at that time I used an older kernel " 5.14.0-1038-oem kernel"
I would if i were you file a bug against kernel  6.5.
FTR I no longer have that laptop as I test hard-ware it was sent to the next victim.

---

### Post by simonsaysthis on 2023-11-16
Thank God I'm not only one who has experienced this. Your suggestion about the bug report makes sense but I am not sure if its a general Kernel 6.5 issue or just an Ubuntu Kernel 6.5 issue. On Fedora with 6.5 the thermals and fan control are even better than Windows. So either they have applied some patch benefiting this CPU or something is wrong with the Ubuntu Kernel.

---

### Post by MAFoElffen on 2023-11-16
> **simonsaysthis said:**
> Thank God I'm not only one who has experienced this. Your suggestion about the bug report makes sense but I am not sure if its a general Kernel 6.5 issue or just an Ubuntu Kernel 6.5 issue. On Fedora with 6.5 the thermals and fan control are even better than Windows. So either they have applied some patch benefiting this CPU or something is wrong with the Ubuntu Kernel.
I don't care if 6.5 is having problems in other Distro's or not. That doesn't matter. The issue is that it is having a problem in Ubuntu, and that is what you are using. That may be just a compile option they set when they compiled it for Ubuntu. Or it may be something in the kernel code itself when it hits a perfect-storm combination of hardware, and drivers.

Let the Launchpad Members figure that out.

---

### Post by simonsaysthis on 2023-11-16
> **MAFoElffen said:**
> I don't care if 6.5 is having problems in other Distro's or not. That doesn't matter. The issue is that it is having a problem in Ubuntu, and that is what you are using. That may be just a compile option they set when they compiled it for Ubuntu. Or it may be something in the kernel code itself when it hits a perfect-storm combination of hardware, and drivers.

Let the Launchpad Members figure that out.

Thanks. Valid point. Any suggestions what would be the most important information to include when submitting the bug report so that the members have enough info to investigate?

---

### Post by Yellow Pasque on 2023-11-16
Before you file a bug, check the CPU usage (with htop). Maybe there's no issue with the kernel or fan control, but instead, you have some process pegging the CPU and causing the fan to run that fast.

---

### Post by MAFoElffen on 2023-11-16
I usually try to diagnose things, and look for a work-arounds, unless I see something seriously wrong that should be corrected in the code. 

The key in the description here was on "startup", then "constantly from there on"... With that description, something is very wrong with the code with this machine...

I can see the fans spinning up at first on start, on server boards... or spinning up when things get how, or under a heavy load. But constantly? That indicates bug somewhere.

---

### Post by Yellow Pasque on 2023-11-16
I wasn't suggesting that it wasn't a bug or not to file a bug. I was suggesting doing some basic diagnosis to see if the problem is the kernel or another package.

---

### Post by MAFoElffen on 2023-11-16
> **Yellow Pasque said:**
> I wasn't suggesting that it wasn't a bug or not to file a bug. I was suggesting doing some basic diagnosis to see if the problem is the kernel or another package.
+1 -- Very true. That would help with the bug report, and narrow down what to file it against.

---

### Post by #&amp;thj^% on 2023-11-16
> **MAFoElffen said:**
> I usually try to diagnose things, and look for a work-arounds, unless I see something seriously wrong that should be corrected in the code. 

 But constantly? That indicates bug somewhere.
That's the key. and don't forget "the welcome app freezes on first boot."
On a *fresh/new* install without any Gnome or snaps, my fans spin higher more than I've ever noticed.
But mine was due to setting CPU scaling to performance in grub, and temps with a load hovered in the 70'sC range.
On all my upgraded systems  to noble nothing like that is present on kernel 6.5....Go figure.

---

### Post by simonsaysthis on 2023-11-17
Thanks everyone for all the valuable input. I just installed 23.10 again to file the bug report but the problem magically vanished. I honestly have no explanation for the sudden change. Before that I had tried at least 7 times and the constant fan spinning at maximum was always present. The welcome app froze again this time but everything else is working fine.

Here are the only error messages from the Kernel I can see

sudo dmesg --level=err

> [    8.664697] spi-nor spi0.0: unrecognized JEDEC id bytes: f6 f0 30 09 03 00
[    9.080077] iwlwifi 0000:00:14.3: WRT: Invalid buffer destination
[   10.177656] Bluetooth: hci0: Malformed MSFT vendor event: 0x02
[   10.562947] iwlwifi 0000:00:14.3: WRT: Invalid buffer destination
[42888.104684] iwlwifi 0000:00:14.3: WRT: Invalid buffer destination
[42981.591657] iwlwifi 0000:00:14.3: WRT: Invalid buffer destination


 sudo dmesg -l warn | head -2

> 
[    0.119656]   #1  #3
[    0.141585] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'

---

### Post by MAFoElffen on 2023-11-17
I'll file a bug against the welcome app. Since the DEV Noble Daily iso is now working, that is even more apparent, and being a pain with that... 

It gets an error, and says it is "not responding", asking if you want to kill it or wait. That is what you are describing right?

That will get more weight with that, since it will be an LTS. Then the fix for that can get backported to Mantic.

---

### Post by simonsaysthis on 2023-11-17
> **MAFoElffen said:**
> I'll file a bug against the welcome app. Since the DEV Noble Daily iso is now working, that is even more apparent, and being a pain with that... 

It gets an error, and says it is "not responding", asking if you want to kill it or wait. That is what you are describing right?

That will get more weight with that, since it will be an LTS. Then the fix for that can get backported to Mantic.

Will do so. It's exactly what's happening on my side. I even discovered another odd bug. I have an external 4k monitor. If I boot into live and use normal scaling at 200% then the flutter-based installer will not load anymore. Just keeps spinning. It only works if I leave it unscaled and install immediately. Not using scaling, closing the installer and reopening will also lead to the infinite loading spin. I tested if logging out and back in will make the installer load again but even that doesn't work. Very odd but could have an X11 bug since live boots into that not Wayland.

---

### Post by MAFoElffen on 2023-11-17
Filed: [https://bugs.launchpad.net/subiquity/+bug/2043838](https://bugs.launchpad.net/subiquity/+bug/2043838)

Please join this Bug as affected.

---

