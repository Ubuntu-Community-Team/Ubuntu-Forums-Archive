---
title: "webcamera is not available from time to time"
date: 2018-07-27
forum: General Help
---

### Post by marchello_lippi2 on 2018-07-27
Hi all, 
My webcamera is not available from time to time. Reboot does help. Who experienced something similar, how do I fix this? Mb there is some way to fix it w/o need to reboot... Please advise.

---

### Post by mörgæs on 2018-07-28
Which camera and which release of Buntu?

Please post in CODE tags the output from ```
lsusb
``` and ```
uname -a
```

---

### Post by marchello_lippi2 on 2018-08-05
> **mörgæs said:**
> Which camera and which release of Buntu?
Hi, sorry for delay, was on vacation. 
So.. checked in cheese program, it says that camera is not found, lsusb does not say much as well, will try again after reboot. 
```

$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1a2c:4c5e China Resource Semico Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
$ uname -a
Linux marchello 4.4.0-130-generic #156-Ubuntu SMP Thu Jun 14 08:53:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mörgæs on 2018-08-06
These "some times it works, some times it doesn't"-errors are difficult to diagnose. First, is there any difference if you try a live boot of 18.04?

---

### Post by marchello_lippi2 on 2018-08-06
> **mörgæs said:**
> These "some times it works, some times it doesn't"-errors are difficult to diagnose. 
Agree.
> First, is there any difference if you try a live boot of 18.04?
Will check and update here.

---

### Post by HermanAB on 2018-08-06
Howdy,

You can get the same effect as a reboot, by removing and reloading the relevant kernel module with rmmod and lsmod, but which one exactly it is, will require some sleuthing:
# lsmod:
...
uvcvideo               86930  0 
videobuf2_vmalloc      13788  1 uvcvideo
videobuf2_core         49196  1 uvcvideo
videobuf2_memops       13161  1 videobuf2_vmalloc
v4l2_common            13919  1 videobuf2_core
videodev              152428  3 uvcvideo,v4l2_common,videobuf2_core
media                  20967  2 uvcvideo,videodev
...

---

