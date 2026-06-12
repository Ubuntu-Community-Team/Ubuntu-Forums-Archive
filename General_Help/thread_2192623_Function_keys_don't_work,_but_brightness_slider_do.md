---
title: "Function keys don't work, but brightness slider does"
date: 2013-12-08
forum: General Help
---

### Post by xmbwd on 2013-12-08
I'm on a Asus, and I'm having the same problem. I made the grub mod suggested above and rebooted, but the problem reamined.  

Here is the laptop's montior information.


Any help would be greatly appreciated.  As the OP stated, the display can be dimmed in the System Settings, but the keyboard command does not work (dim or brighten).  Interestingly, the keyboard commands for key backlight works as does turning the screen off entirely.

---

### Post by Toz on 2013-12-08
*I've moved this post to a thread of its own. Originally posted in [http://ubuntuforums.org/showthread.php?t=2145241]("http://ubuntuforums.org/showthread.php?t=2145241")*

Can you provide some more information? Specifically:

1. The make and model of your computer.

2. The version and flavour of ubuntu that you are using?

3. Your current kernel boot line:
```
cat /proc/cmdline
```

4. Your video card and driver:
```
lspci -k | grep -iA2 VGA
```

5. Your backlight interfaces and their values:
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```

---

