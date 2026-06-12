---
title: "Brightness Control: Brightness Jumping with Fn- keys"
date: 2013-07-17
forum: General Help
---

### Post by frankenfart on 2013-07-17
Hi, when I change brightness through the Fn- keys the brightness jumps at weird intervals.

When it is at 0%, I can press Fn-Down (normally supposed to reduce brightness) and it alternates between 10% and 40% after first going up to 50%. 
However when it is at 100%, Fn-Up (which increases brightness) leaves the brightness at 100% (as it should).

When I press the Fn- keys to change brightness at any other brightness percentage, I get annoying results.

From testing, these are some of the scenarios.

Pressing Fn-Down repeatedly alternates between 10% and 40%.
Pressing Fn-Up from 10% increases it to about 80%.
Fn-Up again gives 100%.
Fn-Down decreases it to 80%, again and it becomes 50% or so.

As you can see, there is no constant interval for brightness control with Fn- keys for me.

I am using proprietary Nvidia driver 325.08 (although I experience the same issue when using the default drivers).
The graphics card is a GTX 460M. 
Laptop model is an MSI-Force16F2.

What can I do to fix this?
Please post what I need to do in case you need me to do diagnostics.
Thanks

---

### Post by Toz on 2013-07-17
Hello and welcome to the forums.

Can you provide the following information (open a terminal window, type in the following commands and post back the results):

1. You kernel boot line:
```
cat /proc/cmdline
```
2. Information about your video card/driver:
```
lspci -nnk | grep -A3 VGA
```
3. Information about your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
4. Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

