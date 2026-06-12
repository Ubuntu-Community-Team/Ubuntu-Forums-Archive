---
title: "Random Freezes with new build:  authoritative AMDGPU installation instructions?"
date: 2023-10-09
forum: General Help
---

### Post by scottie-z on 2023-10-09
As the title suggests, I have a new build experiencing random freezes.  My main concern is ruling out a hardware issue.  System specs:


[LIST]
[*]Ubuntu 22.04 LTS 
[*]ASRock B650M-HDV/M.2 
[*]Ryzen 7800x3d 
[*]Radeon 7800xt 
[/LIST]

Based on what I have read, I suspect the graphics driver stack simply hasn't caught up to the (recent) hardware yet.  I've attempted to update things to newer versions, but I'm finding references to lots of different components and procedures, including:


[LIST]
[*]the kernel 
[*]the drivers themselves (amdgpu) 
[*]an associated kernel module (amdgpu-dkms) 
[*]possibly relevant firmware (linux-firmware) 
[/LIST]

The [official AMD installation instructions]("https://www.amd.com/en/support/kb/faq/amdgpu-installation") only seem to refer to the drivers themselves, but forum posts on similar topics seem to suggest that all four of these may require updates.  So far, I have 


[LIST]
[*]installed the latest drivers from AMD 
[*]installed kernel 6.5 (apt install linux-oem-22.04d) 
[*]checked for firmware updates using fwupdmgr (none found) 
[*]been unable to see any option for updating amdgpu-dkms 
[/LIST]

in that order, but freezes persist, and at this point it feels like I'm just trying random things that are as likely to break the system as fix it.  I had hoped to find an unambiguous set of installation instructions that discuss each of the four components (and any others needed), but lots of searching hasn't turned up anything.

Thanks in advance for any wisdom.

---

### Post by MAFoElffen on 2023-10-10
Please post the output of this within CODE Tags:
```

uname -r
lsb_release -d
apt list linux-firmware --installed
apt list linux-generic-hwe-* --installed
sudo lspci -vvk | grep -i -e '^[0-1][0-9]\:[0-9][0-9]\.[0-9]' -e 'Subsystem\|Kernel' | grep -i -A3 -E 'Display|VGA |3D'

```

---

