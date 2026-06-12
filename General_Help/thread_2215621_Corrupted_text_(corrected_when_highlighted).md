---
title: "Corrupted text (corrected when highlighted)"
date: 2014-04-07
forum: General Help
---

### Post by will29 on 2014-04-07
New after I upgraded to Saucy:
Text display becomes garbled (sometimes as I am typing it).


Example:[IMG]http://imagebin.org/index.php?mode=image&id=304279[/IMG]
[IMG]https://farm8.staticflickr.com/7111/13696971754_d4766ac2fd_o.png[/IMG]

NOTE: The garbled text is corrected when refreshed, highlighted, or additional text typed.

Any idea what may cause this?
Does Saucy has a new font rendering engine or settings?

---

### Post by Toz on 2014-04-07
Hello and welcome to the forums.

What kind of video card do you have? Entering this command in a terminal window will identify the card and the driver being used:
```
lspci -k | grep -iA2 VGA
```

If you have an intel video card, the default acceleration method in saucy was changed to SNA (from UXA), and this causes problems on some intel adapters like you are noticing. To see which acceleration method your system is using:
```
cat /var/log/Xorg.0.log | grep -i accelmethod
```

The fix is to revert to the UXA acceleration method.

---

### Post by will29 on 2014-04-07
lspci -k | grep -iA2 VGA 

reveals:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Lenovo Device 2115
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV635/M86 [Mobility Radeon HD 3650]
    Subsystem: Lenovo Device 2126


This seems to confirm that SNA is being used:
> less /var/log/Xorg.0.log |grep SNA
[     6.398] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.904-0ubuntu2.1 (Robert Hooker <sarvatt@ubuntu.com>)
[     6.401] (II) intel(0): SNA initialized with Eaglelake (gen4.5) backend



I'll revert back to UXA and see if that fixes the issue.

Thank you very much!

---

