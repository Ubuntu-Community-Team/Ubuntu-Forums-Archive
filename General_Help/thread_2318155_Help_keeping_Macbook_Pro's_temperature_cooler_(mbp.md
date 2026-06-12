---
title: "Help keeping Macbook Pro's temperature cooler (mbpfan)"
date: 2016-03-23
forum: General Help
---

### Post by brandonhughes1811 on 2016-03-23
Hi! I dual booted Ubuntu with OSX using direct EFI boot. And once I got everything installed, updated, etc, I noticed that my mac would heat up pretty fast. I installed and configured "mbpfan" and got it working. But I want to know if there's anything more I can do?

In OSX, the temperature would stay between 45-55 even with safari running and normal usage. The fans would run at 2000rpm which wasn't noticeable (it was quiet).
On ubuntu, it would go up to 65 on idle, with nothing running at all. 

This is how I set uo mbpfan.conf afterwards:

[general]
min_fan_speed = 4200    # default is 2000
max_fan_speed = 7600    # default is 6200
low_temp = 40                   # try ranges 55-63, default is 63
high_temp = 50                  # try ranges 58-66, default is 66
max_temp = 65                   # do not set it > 90, default is 86
polling_interval = 7    # default is 7

With this configuration, it manages to stay at 55 degrees with normal use, but that's with the fans running at 7000rpm. 

The noise doesn't bother me that much, i'd rather keep the temperature under control. But something has got to be making the temperature jump because just booting into ubuntu will jump it up to 60 (before the fans kick in). That's why I keep the minimum fan rpm so high at 4200.

Nothing in "top" is showing that an application or process is taking a lot of cpu, everything seems normal.

So if you have any tips at all, please let me know :) I can provide more information if you like. Thank you!

---

