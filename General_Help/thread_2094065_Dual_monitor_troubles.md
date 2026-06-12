---
title: "Dual monitor troubles"
date: 2012-12-12
forum: General Help
---

### Post by Aqlor on 2012-12-12
Hello good people.

After some time without an ubuntu distro, I decided to come back and I installed the latest Ubuntu version last week on my EEEPC.

Now, I am having some problems with my dual screen configuration.

If I boot the laptop with the monitor connected for the first time, everything will be ok. However, if I shutdown my computer without changing this configuration, the next time I boot it, I will congratulated with two boring black screens.

So this is what happens.

Computer + no external monitor - boots normally
Computer + other monitor(1st time) - boots normally
Computer + other monitor(2nd time) - two black screen

I thought this would be something recoverable from the command line (isn't everything) so I tried pressing Alt+Ctrl+F1 to go to the first tty. 
Instead, the monitors "flashed", just like they would if changing the resolution but the blackness stayed there.

Now my only option is to shutdown the hard way, so the monitors work again next time.

Is this a known bug?

Thank you


```
uname -a
Linux ____ 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
```

levi@levi:~$ xrandr 
Screen 0: minimum 320 x 200, current 1680 x 1536, maximum 8192 x 8192
LVDS connected 1366x768+0+768 (normal left inverted right x axis y axis) 270mm x 150mm
(...)
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 465mm x 291mm
(...)

```

---

