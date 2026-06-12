---
title: "Brightness control...."
date: 2015-08-18
forum: General Help
---

### Post by dsuresh on 2015-08-18
hi,  i just installed xbuntu 15.04..  brightness control not working.. 

my old thread  [http://ubuntuforums.org/showthread.php?t=1866283](http://ubuntuforums.org/showthread.php?t=1866283)  was works on xubuntu 12+ version...

now this settings not working....  someone help me....

SAMSUNG N148 NETBOOK

Thanks in advance

---

### Post by Toz on 2015-08-18
What do the following commands return?

```
uname -a
```
```
cat /proc/cmdline
```
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
```
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by dsuresh on 2015-08-18
hi, thanks for your valuable reply..

_**[COLOR="#FF0000"]$[/COLOR]**_ uname -a
Linux admini-N148P 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:01 UTC 2015 i686 i686 i686 GNU/Linux

**_[COLOR="#FF0000"]$[/COLOR]_** cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=12cb161b-cfa3-41da-8339-8269e9ae8fde ro acpi_backlight=vendor quiet splash vt.handoff=7


_**[COLOR="#FF0000"]$[/COLOR]**_ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/intel_backlight
12421
12421
12421

 /sys/class/backlight/samsung
0
8
0



**_[COLOR="#FF0000"]$[/COLOR]_** cat /var/log/Xorg.0.log | grep -i backlight
[  6825.192] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=12cb161b-cfa3-41da-8339-8269e9ae8fde ro acpi_backlight=vendor quiet splash vt.handoff=7
[  6825.219] (--) intel(0): Found backlight control interface samsung (type 'platform') for output LVDS1

---

### Post by Toz on 2015-08-18
With root privileges, create a **/usr/share/X11/xorg.conf.d/20-intel.conf** file with the following content:
```
Section "Device"
        Identifier "card0"
        Driver "intel"
        Option "Backlight" "intel_backlight"
        BusID "PCI:0:2:0"
EndSection
```

Log out and back in again and see if it helps.

---

### Post by dsuresh on 2015-08-18
its working.. thank you.....:)   :cool:

---

