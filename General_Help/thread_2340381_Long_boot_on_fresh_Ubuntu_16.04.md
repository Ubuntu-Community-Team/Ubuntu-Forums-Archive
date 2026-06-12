---
title: "Long boot on fresh Ubuntu 16.04"
date: 2016-10-18
forum: General Help
---

### Post by alexb888 on 2016-10-18
I installed Ubuntu 16.04.1 using mini.iso on Lenovo ThinkPad X230 (installed only base system and then installed other packages manually) and boot time is very long
```
$systemd-analyze
Startup finished in 3.521s (firmware) + 3.481s (loader) + 2.032s (kernel) + 3min 586ms (userspace) = 3min 9.622s
```

Here is what systemd-analyze shows: [systemd-analyze blame, ]("http://pastebin.com/tnQUwHzc")[systemd-analyze plot]("http://svgur.com/i/CP.svg"). If I understand plot correctly there is a delay because of initialization of device (looks like this is bluetooth controller)
```
sys-devices-pci0000:00-0000:00:1a.0-usb1-1\x2d1-1\x2d1.4-1\x2d1.4:1.0-bluetooth-hci0.device
```
I tried to turn off bluetooth.service but this does not help.

Then I looked at [dmesg]("http://pastebin.com/R95shqWi") and there is another place with big delay between trackpoint initialization and AppArmor initialization
```
/platform/i8042/serio1/serio2/input/input7
[   92.438151] audit: type=1400 audit(1476684183.179:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=613 comm="apparmor_parser"

```

Any ideas what is wrong and how I can fix it?

---

