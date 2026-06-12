---
title: "[ubuntu] ASUS Zenbook ux303 - power saving (ASPM/ALPM)"
date: 2015-04-13
forum: General Help
---

### Post by c51 on 2015-04-13
Hi,

anybody out there who already successfully optimized runtime on battery?

Just wondering if the [suggestions I found]("https://help.ubuntu.com/community/AsusZenbook#Kernel_parameters_to_use") still hold true for the newer UX303 Zenbook (as on top of the page the addressed models are UX31E/UX21E).
And: **are they even necessary** with Ubuntu 14.04 (3.16.x kernel)?:
**[...].**


[COLOR=#333333][FONT=Ubuntu]After enabling also the optimizations below, one should get circa 5W idle power usage with screen on but brightness to minimum, with WLAN connected.

[...][/FONT][/COLOR]
**Enabling ASPM saves a meaningful amount of power when idle according to powerstat. It's recommended. The pcie_aspm=force parameter is however required on Zenbook because the Zenbook BIOS gives Ubuntu wrong information. Therefore, add the following to the file[FONT=inherit]/etc/default/grub[/FONT], after the text [FONT=inherit]quiet splash[/FONT] but within the same quotes:**



pcie_aspm=force[COLOR=#333333][FONT=Ubuntu]There are a couple of optional kernel parameters which save some power and have not shown any problems with Zenbook, but are not enabled by default. Instead of the above, you may also use the following:[/FONT][/COLOR]
pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1
I tried with none of the options,only with forcing aspm and also with all the options mentioned at the end.

Having disabled keyboard backlight, WLAN, Bluetooth, Dispalay dimmed max, and ran "powertop --auto-tune" before running powerstat and the drain is still about ~8.6W (compared to the aforementioned 5 Watts with connected wifi).

Anybody willing to share his/her experiences?

Regards,
c51

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  
[B]Edit:
[/B]
just found this in my logs:
```

[ 2817.029086] ata1.00: exception Emask 0x10 SAct 0x100 SErr 0x50000 action 0xe frozen
[ 2817.029093] ata1: SError: { PHYRdyChg CommWake }
[ 2817.029101]          res 40/00:44:28:ff:5b/00:00:08:00:00/40 Emask 0x10 (ATA bus error)

```
I think this is related to testing ALPM.... disabling again....

---

### Post by c51 on 2015-04-14
Progress:

It seems that my nvidia driver was not installed correctly. Now - and with nvidia prime - the nvidia graphics card gets disabled which reduced the power consumption to ~6.1W.

According to powerstat the best result so far was 5.6W:
- backlight dimmed max running [FONT=courier new]intel_backlight 1[/FONT] which further dimms from 4% to 1%
- disabling keyboard backlight
- disabling Bluetooth, LAN & Wifi
- running [FONT=courier new]powertop --auto-tune[/FONT] [FONT=arial]prior to[/FONT] [FONT=courier new]powerstat[/FONT]

Last possibility to tweak might be undervolting the CPU using phc-intel driver. Unfortunately this is not possible with standard ubuntu kernel, as acpi_cpufreq gets compiled into kernel by default making it impossible to blacklist the module in order to load phc-intel...

---

