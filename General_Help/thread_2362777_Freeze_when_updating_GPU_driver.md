---
title: "Freeze when updating GPU driver"
date: 2017-06-01
forum: General Help
---

### Post by thanekrios on 2017-06-01
I'm on Ubuntu 16.04.2 64 bit. Whenever I try to install my _GPU drivers_, it starts, goes on for a while and then freezes,_ this happens on all variants_ This is my computer:
[B]
CPU: AMD - FX-8350 4.0GHz 8-Core Processor [/B]
CPU Cooler: Deepcool - GAMMAXX 400 74.3 CFM CPU Cooler 
**Motherboard: Gigabyte - GA-970A-DS3P ATX AM3+ Motherboard rev 2.x**
Memory: Kingston - HyperX Fury Red 8GB (2 x 4GB) DDR3-1866 Memory
Storage: Sandisk - SSD PLUS 240GB 2.5" Solid State Drive
**Storage: Seagate - Barracuda 500GB 3.5" 7200RPM Internal Hard Drive (this is the disk I installed on)**
**Video Card: MSI - GeForce GTX 1060 6GB 6GB OCV1 Video Card **
Case: Raidmax - Narwhal ATX Full Tower Case 
Power Supply: EVGA - 500W 80+ Certified ATX Power Supply  

Thanks for any help you can provide!

---

### Post by thanekrios on 2017-06-04
Bump

---

### Post by thanekrios on 2017-06-05
bump

---

### Post by Bashing-om on 2017-06-05
thanekrios; Hello;

Situation: hybrid graphics, and with AMD in the midst of their changes to support open source - many ( including me ) do not have a grasp on what can be done.

But, let's start this ball rolling to see what we can do /
Post back - Between Code Tags - the outputs of terminal commands:
```

lspci -k | grep -EA2 'VGA|3D'
lsmod | grep radeon
lsmod | grep amdgpu
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Where we look at what hardware the system is aware of and if the appropriate drivers are installed.

[INDENT][INDENT]in that process of learning
[/INDENT][/INDENT]

---

### Post by oldrocker99 on 2017-06-05
He does have a nVidia 1060, no hybrid graphics. Is the OP installing the drivers from the repositories or from nVidia's website? It's a lot safer to use the repositories.

---

### Post by zozio32 on 2017-06-05
something similar happen to me on 17.04.
Did not work through the aditional driver stuff in synaptic package manager, but by choosing the nvidia 375 package straight into the repositories with Synaptic Package manager, it works without problem.

---

### Post by thanekrios on 2017-06-06
Ok guys. I reinstalled Lubuntu x64 17.04 with some different BIOS settings, and this time it worked. I've tried reinstalling before, different flavours and all, and still no luck, so I'm going to rule out chance, and call it dumb luck. Just in case anyone cares I'll detail what I did:

[LIST]
[*]Enabled CSM
[*]Disabled Secure boot
[*]Changed from ACHI to IDE
[*]Enabled IOMMU (seems mandatory for x64 .iso's, or otherwise it won't recognize the USB)
[*]Used nomodeset installation
[*]Installed without Internet connection and unchecked "Install third party software"
[*]Installed the drivers without synaptic
[/LIST]

I have to say, I couldn't have chosen worse hadware to install Ubuntu on. It's been hell.

Anyways I appreciate all your help and attempts, and I'm not even sure I fixed it, but Lubuntu is up and running, so thanks everyone!

---

### Post by Bashing-om on 2017-06-06
thanekrios !

:)

-when at 1st you do not succeed-

---

