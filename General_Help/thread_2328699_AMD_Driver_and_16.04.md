---
title: "AMD Driver and 16.04"
date: 2016-06-23
forum: General Help
---

### Post by jub2 on 2016-06-23
The 14.04 drivers from AMD won't work at all in Ubuntu 16.04?

I was thinking about installing Ubuntu 16.04 on a system with a Radeon HD 6450 card. In a live ISO session, some default Radeon driver was loaded (open source Radeon driver I guess) and the 2 monitors attached to the Radeon card (3 monitor setup) weren't working properly. 

I was hoping the AMD Ubuntu 14.04 proprietary drivers would solve this, but if they won't work, maybe I'll just stick with Windows on this particular machine. Or maybe check out 14.04, though I'm sure it will feel old since I'm running 16.04 on another machine.

---

### Post by banceu_sergiu_ione on 2016-06-23
Had you try to update Mesa with Padoka PPA. 

Thought System Settings - Display you can easy control the resolution of all connected displays, with or without property graphic drivers.

[AMD GPU - PRO BETA Driver]("http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Beta-Driver-for-Vulkan-Release-Notes.aspx") is already up for install on linux but it only support R9 family at the moment. Give few months and will going to support more classes.

Anyway, 16.04 with mesa, standing at [phoronix test]("http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1") it compare much better then 14.04 with fglrx.

---

### Post by jub2 on 2016-06-23
> **banceu_sergiu_ione said:**
> Had you try to update Mesa with Padoka PPA. 

Thought System Settings - Display you can easy control the resolution of all connected displays, with or without property graphic drivers.

[AMD GPU - PRO BETA Driver]("http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Beta-Driver-for-Vulkan-Release-Notes.aspx") is already up for install on linux but it only support R9 family at the moment. Give few months and will going to support more classes.

Anyway, 16.04 with mesa, standing at [phoronix test]("http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1") it compare much better then 14.04 with fglrx.Not sure if you are responding to my post or an earlier post. 

I used Display, and while it can control the resolution of the connected displays, it cannot correctly identify them or rotate them. Also, it's very fragile with the open source driver and easily crashes. Is that something updating Mesa could fix?

I don't need the ability to play games or run cad programs. But I do need the ability to rotate at least one of the displays connected to the AMD card and for it to be relatively stable.

---

### Post by QIII on 2016-06-23
Moved to its own thread from [http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075)

---

### Post by jub2 on 2016-06-23
> **QIII said:**
> Keep an eye out.  The scuttlebutt indicates an fglrx returning at the first point release.  Possibly.  Maybe.@QIII, I saw you were involved in the process to get the fglrx install bug/issue on 14.04.2 resolved.

I'm trying to install fglrx, but having some trouble. I updated [COLOR=#333333][FONT=monospace]/etc/apt/sources.list to include:
[/FONT][/COLOR]```
[COLOR=#333333]deb http://archive.ubuntu.com/ubuntu/ trusty-released restricted main multiverse universe[/COLOR]
```
then ```
sudo apt-get update
```
then ```
sudo apt-get install fglrx-updates/trusty-released
```

also tried ```
sudo apt-get install fglrx/trusty-released
```

No joy either way as neither package is found:
[[IMG]http://i175.photobucket.com/albums/w128/pbucket_pics/misc/desktoptrustyreleased.png[/IMG]]("http://s175.photobucket.com/user/pbucket_pics/media/misc/desktoptrustyreleased.png.html")

Where am I going wrong? This is an install on a USB flash drive, if that might the problem (full install of Xubuntu 14.04.3 onto the flash drive, not just a live ISO).

---

### Post by QIII on 2016-06-23
Merged here from [http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075)

Please do not hijack that thread.

---

### Post by jub2 on 2016-06-23
sorry, misunderstood what you meant by the prior "merged from here" post. Got it now.

So I was able to install from Synaptic, so I guess the fixed fglrx got moved out of -proposed, then got moved out of -released to wherever it goes next in the line of becoming a 'production' driver.

---

### Post by grahammechanical on 2016-06-23
Check in Software & Updates that Proprietary drivers for devices (restricted) is enabled. You might want to use Additional Drivers to install the proprietary video driver.

Regards.

---

### Post by Yellow Pasque on 2016-06-24
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)
There is no 'trusty-released' (it's just 'trusty).
Anyway, I doubt that version of fglrx is going to work in 16.04 (kernel and/or X versions too new), or Ubuntu would have included it there.

You've got two options:
1. Use 14.04.x
2. Use 16.04 with open source radeon driver. If it doesn't work right, set about getting the bugs fixed.

> AMD GPU - PRO BETA Driver is already up for install on linux but it only support R9 family at the moment. Give few months and will going to support more classes.
Support is planned for cards based on GCN 1.0 and newer. The RadeonHD 6450 is a bit too old for that.

---

### Post by jub2 on 2016-06-24
> **Temüjin said:**
> [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)
There is no 'trusty-released' (it's just 'trusty).Thanks for the explanation.

> **Temüjin said:**
> 
Anyway, I doubt that version of fglrx is going to work in 16.04 (kernel and/or X versions too new), or Ubuntu would have included it there.Yeah, it can't be installed in 16.04.

> **Temüjin said:**
> You've got two options:
1. Use 14.04.x
2. Use 16.04 with open source radeon driver. If it doesn't work right, set about getting the bugs fixed.


Support is planned for cards based on GCN 1.0 and newer. The RadeonHD 6450 is a bit too old for that.I've got fglrx-updates loaded in 14.04.4. And it drives the two monitors I've got connected to the AMD card just fine.

But I'm realizing that the Ubuntu flavors (and perhaps any Linux distribution) cannot run both onboard and discrete graphics simultaneously. Windows 7 can do this, so for this machine, I'll have to stick with Win7 to maintain my triple monitor setup (one monitor driven by Intel onboard graphics, 2 monitors driven by AMD card).

---

