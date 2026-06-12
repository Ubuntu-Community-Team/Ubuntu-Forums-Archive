---
title: "Everytime I upgrade kernels cedarview stops working"
date: 2014-03-07
forum: General Help
---

### Post by Psil0cybin on 2014-03-07
[B][U]
[COLOR=#ff0000]SOLVED 
[/COLOR][/U]Cedar tail does not work with generic-pae, only [COLOR=#008000]generic[/COLOR] kernels. [COLOR=#008000]3.2.x[/COLOR]
[/B]
[B]_Solution:_ If you are using 4gb under, make sure you get the generic versions of the kernel you are having problems installing. (seems to be a package error- cedartail does not like generic-pae?! for some reason)
[/B]
Hey guys everytime I upgrade kernels on my acer aspire one I keep having a cedartail graphic problems.

Going to additional drivers, shows that I can reinstall / activate cedar tail drm driver, but when I do so it says

> 
Sorry, installation of this driver failed.


Please have a look at the log file for details: /var/log/jockey.log


looking inside the jockey log it says

```

2014-03-07 02:02:20,722 DEBUG: Comparing 3.2.0-57 with 
2014-03-07 02:02:20,730 DEBUG: Comparing 3.2.0-58 with 3.2.0-57
2014-03-07 02:02:20,738 DEBUG: Comparing 3.2.0-59 with 3.2.0-58
2014-03-07 02:02:20,747 DEBUG: Comparing 3.2.0-60 with 3.2.0-59
2014-03-07 02:02:23,776 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x963be6c>
2014-03-07 02:02:30,810 DEBUG: reading modalias file /lib/modules/3.2.0-60-generic-pae/modules.alias
2014-03-07 02:02:31,306 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2014-03-07 02:02:31,315 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2014-03-07 02:02:41,806 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2014-03-07 02:02:41,825 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr


2014-03-07 02:02:44,278 DEBUG: linux-lts-raring installed: False
linux-lts-saucy installed: False
linux-lts-trusty installed: False
linux minor version: 2
xserver ABI: 11
xserver-lts-quantal: False
 at 0x963bd0c> about HardwareID('modalias', 'acpi:SYN1B20:SYN1B00:SYN0002:PNP0F13:')
2014-03-07 02:05:41,749 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2014-03-07 02:05:41,752 WARNING: /sys/module/cedarview_gfx/drivers does not exist, cannot rebind cedarview_gfx driver
2014-03-07 02:07:36,293 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2014-03-07 02:07:36,296 WARNING: /sys/module/cedarview_gfx/drivers does not exist, cannot rebind cedarview_gfx driver

```

please help this keeps happening :( I have filed multiple bug reports but every near kernel i upgrade too never fixes this issue, I have to use a very old kernel in order to get my graphics working properly.

---

