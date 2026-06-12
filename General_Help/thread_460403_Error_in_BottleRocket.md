---
title: "Error in BottleRocket"
date: 2007-05-31
forum: General Help
---

### Post by sedition on 2007-05-31
Hi all,

The BottleRocket package (0.05b3-8 on Feisty) generates errors as below. I searched the forums and found a similar entry, but it has been closed. I discovered the error can be generated and corrected when manually by changing the case of specified serial port, i.e.
```
br -x /dev/ttys0 -N
br: error: [Input/output error] Unable to open serial port
```
whilst this works fine:
```
br -x /dev/ttyS0 -N
```
Upon initial install, the package works fine, but after reboot, the program generates the error. Is this a problem with the package compilation? If not/so to whom should it be reported?

Thanks in advance,
-sed

Log:
```

/usr/bin/br: error: [No such file or directory] Unable to open serial port 
/usr/bin/br: error: [No such file or directory] Unable to open serial port 
    while executing
"exec $BottleRocket $House$currentDevice on"
    (procedure "fire_ignite" line 3)
    invoked from within
"fire_ignite $currentHouse 1 $currentRange $bottleRocket"
    invoked from within
".a1.on invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .a1.on"
    (command bound to event)

```

---

