---
title: "ID 046d:0850 Logitech, Inc. QuickCam Web finally works kernel 3.12"
date: 2013-11-29
forum: General Help
---

### Post by sdowney717 on 2013-11-29
after many years this obsolete web cam video finally works.
Sound did not, I am using a microphone. It shows up as a selectable input sound device, but not working.
It needs kernel 3.12 and accelerated Nvidia driver 304
It actually is smooth motioned.
Picture is ok, but it needs a lot of light, dark room is no good.
Since I am getting a new cam, I looked through my old hardware and thought I would try it.
It did not work from kernel 3.2 to 3.7

```
scott@scott-P5QC:~$ lsusb
**Bus 003 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web**
Bus 006 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 006 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
scott@scott-P5QC:~$ 

```

---

