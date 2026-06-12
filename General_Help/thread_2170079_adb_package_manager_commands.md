---
title: "adb package manager commands"
date: 2013-08-24
forum: General Help
---

### Post by Londrioca on 2013-08-24
Ubuntu 12.04 64bit

Downloaded Android Debug Bridge CLI tool from Software centre to enable transfer of apps in Samsung GT15800 Eclair to SD card. USB debugging & Unknown sources enabled in phone but I fall at the last hurdle:

```
:~$ adb
Android Debug Bridge version 1.0.31

:~$ adb devices
List of devices attached 
644259177b23    device

:~$ adb shell
$ pm set-install-location 2          
Error: unknown command 'set-install-location'


```

Same result with pm setInstallLocation 2

What am I missing?

---

