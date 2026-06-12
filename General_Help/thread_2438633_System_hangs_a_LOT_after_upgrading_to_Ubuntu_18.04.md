---
title: "System hangs a LOT after upgrading to Ubuntu 18.04"
date: 2020-03-15
forum: General Help
---

### Post by davy jones on 2020-03-15
I upgraded to Ubuntu 18.04 around a month ago and my system has hung more in this time than it did in the last 5 years. Cursor movements are often jittery and opening multiple apps results in things getting quite slow. At least 3 times it has hung for so long that I've had no choice but to do a hard reboot. Even startup is quite slow. I have no idea what's causing it and I'm not tech-savvy, but here are a few things about my system:

1. I previously had 14.04 alongside Windows 8. I installed 18.04 using the 'something else' option in which I used all the same partitions as I had earlier. But I did not format the /home partition, which saved a bunch of my app settings along with my data. Some of these I deleted based on what apps and services I no longer have in 18.04.

2. I have a Dell Inspiron with hybrid graphics. There's an Intel GPU and a Radeon one. My Ubuntu system does not seem to detect the Radeon one and only uses the Intel one.

Any help would be appreciated.

---

### Post by mörgæs on 2020-03-15
Let's see more of the graphics processors. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by davy jones on 2020-03-16
This is the output for sudo lshw -class display (the command you mentioned wasn't giving an output)

```
*-display                        description: VGA compatible controller
       product: Mars [Radeon HD 8730M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:35 memory:a0000000-afffffff memory:c0000000-c003ffff ioport:3000(size=256) memory:c0040000-c005ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:33 memory:c1000000-c13fffff memory:b0000000-bfffffff ioport:4000(size=64) memory:c0000-dffff
```

It seems to be detecting the Radeon card but when I check go to Settings->Details->About, it says under graphics "Intel Ivybridge Mobile".

---

### Post by mörgæs on 2020-03-16
The command created a file, not terminal output.

Anyway, your graphics processors seem to be fairly standard, and I expect that a fresh install of 18.04.4 or 19.10 (preferably the latter) solves the problem. Don't keep configuration files from old releases.

---

### Post by davy jones on 2020-03-16
Sorry, I realised later that it was a text file!

Do you think I need to re-install 18.04.4 (I already have it and I only install LTS versions) or can I simply delete all the configuration files? Or can I format the /home partition?

---

### Post by sdsurfer on 2020-03-16
I would try something less drastic first. My **guess** is that you are really close . . . 
> when I check go to Settings->Details->About, it says under graphics "Intel Ivybridge Mobile"

My first go-to on any operating system when I have odd freezing behavior is graphics drivers. Make sure that is in order. Though yours is not a Chrome issue, have a look through this recent thread:

[https://ubuntuforums.org/showthread.php?t=2437949](https://ubuntuforums.org/showthread.php?t=2437949)

Particularly, see what this command tells you:
```
lspci | grep VGA
```

Then go in to Search Computer->Software and Updates->Additional drivers and make sure it's using the Radeon driver. I have had conditions where the system is not applying it.

---

### Post by mörgæs on 2020-03-17
> **davy jones said:**
> 

Do you think I need to re-install 18.04.4 (I already have it and I only install LTS versions) or can I simply delete all the configuration files? Or can I format the /home partition?

It's not worth it to put time into these 'compromise' alternatives. Go for the cleanest and most bugfree solution: Fresh install of 19.10 with nothing recycled from the present OS. Takes 20 minutes.

---

### Post by davy jones on 2020-03-17
The output for 

```
lspci | grep VGA
```

is:

```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M]

```

I checked in Additional Drivers and it says that no proprietary drivers are in use and no additional drivers are available. How do I install the driver?

---

### Post by sdsurfer on 2020-03-17
Usually that tells you what driver is in use. Also in that thread are some clues of what to look for in /var/log/syslog as to what is causing the crash, you can snoop around those too. Note the exact time of the freeze, then on reboot dig around in /var/log/syslog (there will be a time gap between the crash and reboot.) There are crash logs too but have found syslog sufficient.

Mostly by chance my hardware has been Nvidia for years, for that reason (and just enough knowledge to keep me out of trouble) I cannot advise on installing and applying Radeon drivers. The place to start is review everything from the manufacturer's page:
[https://www.amd.com/en/support](https://www.amd.com/en/support)

This article looks promising, it's from 2018 and may be outdated but is a pretty clear path.

[https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux)

---

