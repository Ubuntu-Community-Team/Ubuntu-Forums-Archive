---
title: "DPMS disabled while using compiz in kde"
date: 2006-07-31
forum: General Help
---

### Post by joelones on 2006-07-31
hi guys,

I have couple of problems and decided to open up a thread for this in the hope that we can resolve them:

first off, followed this thread to setup compiz:
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_(or_KDM)]("http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_(or_KDM)")

now to the problems,

1) i only see "End Current Session" instead of reboot and shutdown when i attempt to logout in kde, (researched this around the forums and only seems to happen when DISPLAY=:1 is set)

2) DPMS is now not working (was working before), i believe it also has something to do with the DISPLAY=:1 in the following:

```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
```

this is what i get when i issue the command
```
xset dpms force off
```

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  147 (DPMS)
  Minor opcode of failed request:  6 (DPMSForceLevel)
  Serial number of failed request:  10
  Current serial number in output stream:  12

```

forgot to mention using Xinerma for two cloned displays, using lastest quinn's compiz

thanks for the help

---

