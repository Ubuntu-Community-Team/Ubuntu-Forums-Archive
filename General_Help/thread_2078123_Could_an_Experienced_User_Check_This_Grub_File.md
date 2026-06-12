---
title: "Could an Experienced User Check This Grub File?"
date: 2012-10-30
forum: General Help
---

### Post by jakfish on 2012-10-30
Using Lubuntu 12.04 with a Lenovo S10-3t netbook, I'm trying to set up some power-saving commands in my /etc/default/grub file via this helpful link:

[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

This is my grub file:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\" i915.i915_enable_fbc=1 i915.lvds_downclock=1"
GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"

Lubuntu boots and seems fine, but I've never worked with grub before, and wonder if someone more veteran might give this a once-over and let me know if I've set off any alarms.

Many thanks,
Jake

Addendum: I have made certain to run the "sudo update-grub" command

---

### Post by dino99 on 2012-10-30
that wiki is made by a very skilled dev :P
but each hardware has different kernel supported settings, so you only can test the different proposed grub entries and see if it help. Test them one by one first.

And remember that tweak also mean possible breakage (conflict with default other settings into ubuntu or kernel, and/or race conditions, and possible grub bad supporting setting(s))

---

### Post by jakfish on 2012-10-30
I'm grateful for your quick reply.  Certainly, nothing seems broken and the said commands have truly dropped the cpu temperature.

As for the actual syntax in the grub file, especially in the GRUB_CMDLINE_LINUX_DEFAULT line, have I done it right, in your opinion?

Thanks,
Jake

---

