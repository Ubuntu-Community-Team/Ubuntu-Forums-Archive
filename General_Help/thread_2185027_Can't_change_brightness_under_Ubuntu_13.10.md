---
title: "Can't change brightness under Ubuntu 13.10"
date: 2013-10-31
forum: General Help
---

### Post by miguael-bergeron28 on 2013-10-31
Hi, I just installed Ubuntu 13.10 and realized I cannot change the screen brightness (whether it's via keyboard or settings).

I use an Acer 5742. Anyone knowing how to fix that problem ?

Thanks !

---

### Post by Toz on 2013-10-31
Hello and welcome to the forums.

Can we get some more information about your laptop? Open a terminal window, type in the following commands, and post back the results.

1. Your current kernel boot parameter line:
```
cat /proc/cmdline
```

2. Your video card(s) and drivers:
```
lspci -k | grep -iA2 VGA
```

3. Your backlight interfaces and values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

4. Your xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and paste back the link that is generated.

---

