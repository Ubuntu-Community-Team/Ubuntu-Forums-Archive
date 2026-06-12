---
title: "Lenovo Y510P - can't change brightness in Ubuntu 13.10"
date: 2013-12-04
forum: General Help
---

### Post by radenkovich on 2013-12-04
Please help me, I really enjoy Ubuntu 13.10 on this laptop but screen brightness is burning my eyes! 
I managed to reduce brightness and contrast using NVIDIA X Server Settings but I do not really fill like actual brightness is reduced, my mouse cursor (arrow) is very bright white (looks kind a funny)...
Brightness slider in Ubuntu no effects, Fn+arrow key press is deteced by Ubunty but no changes in brightness at all...

1.
**Lenovo IdeaPad y510p**

2.
```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic.efi.signed root=UUID=aec56d0c-f753-4e40-948a-34e69d7dfca6 ro
```

3.
```
lspci -k | grep -iA2 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
    Subsystem: Lenovo Device 3800
    Kernel driver in use: nvidia
```

4.
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
0
100
```

5.
```
pastebinit /var/log/Xorg.0.log
[http://paste.ubuntu.com/6521767/](http://paste.ubuntu.com/6521767/)
```

---

### Post by Toz on 2013-12-04
*Post moved to its own thread.*

I was recently involved in trying to fix the brightness issue for this device (see: [http://ubuntuforums.org/showthread.php?t=2167180]("http://ubuntuforums.org/showthread.php?t=2167180")). Unfortunately, there was no immediate "fix" available, however, if you look at post #24, there are some instructions on using xbacklight to at least get you control of the screen brightness.

Somebody (who owns the device) should create a bug report on launchpad.net for this.

---

### Post by radenkovich on 2013-12-04
i would fill a bug, any advice how to proceed?

---

### Post by Toz on 2013-12-04
From a terminal window, run:
```
ubuntu-bug linux
```
...to get the process started. More info [here]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by radenkovich on 2013-12-05
done, thanks!
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1258058](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1258058)

---

