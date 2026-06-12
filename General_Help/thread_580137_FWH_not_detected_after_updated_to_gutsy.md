---
title: "FWH not detected after updated to gutsy"
date: 2007-10-18
forum: General Help
---

### Post by weekendli on 2007-10-18
Hey all,

After a brand new installation from live CD into ubuntu 7.10, there are still some problems laying around on my machine.

1. When the machine reboot, it frozen on the stage of loading kernel. I need to manually switch into terminal mode to let the booting carry on, the only message I got is "FWH not detected", not sure is it the relative error message. I also can see the splash booting screen as well. 

2. After the machine booted into gnome, the small splash image indicate gnome's loading also disappeared. not sure why? 

Things' going very well on my machine with 7.06, it's still little bit buggy on 7.10 for me, do you know how can I make it perfect. thanks

jian

---

### Post by newcoventry on 2007-11-08
I am experiencing really slow boot times too.  When I suppress the splash screen, I notice that it is taking a lot of time on 

[12.288000] intel_rng: FWH not detected

Any ideas how to resolve this?

---

### Post by newcoventry on 2007-11-09
I managed to find a work around, although I am not sure how well it will work long term.
I added the module to the modprobe blacklist by doing the following:
```

sudo nano -w /etc/modprobe.d/blacklist

```

At the end of the file type:

```

# intel_rng seems to slow boot
blacklist intel_rng

```

Now the computer does not attempt to load intel_rng and my boot time is a bit faster.

---

### Post by mrmudman56 on 2008-03-02
On DELL Dimension with PIII Coppermine:
Linux XXXXXX  2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
orig install:

[   41.504705] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   41.518532] input: PC Speaker as /class/input/input2
[   42.105623] iTCO_vendor_support: vendor-support=0
[   42.118544] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   42.250297] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   42.250405] iTCO_wdt: No card detected
[   42.592546] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   42.592554]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   42.592559]  you are certain that your <4>intel_rng: system has a functional
[   42.592563]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   43.982320] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
--------------------------------------------------------------------------------------------------
Edited /etc/modprob.d/options
added line
options intel_rng no_fwh_detect=1
Then executed
sudo update-initramfs -u
and rebooted

Now I get:
---------------------------------------------------------------------------------------------------

[   37.613895] i810_smbus 0000:00:01.0: i810/i815 i2c devi
ce found.
[   37.856548] iTCO_vendor_support: vendor-support=0
[   37.869154] iTCO_wdt: Intel TCO WatchDog Timer Driver v
1.01 (21-Jan-2007)
[   37.906298] iTCO_wdt: failed to reset NO_REBOOT flag, r
eboot disabled by hardware
[   37.906413] iTCO_wdt: No card detected
[   37.960396] Intel 82802 RNG detected
[   40.325818] input: PC Speaker as /class/input/input2
[   41.050252] input: ImPS/2 Generic Wheel Mouse as /class
/input/input3

---

