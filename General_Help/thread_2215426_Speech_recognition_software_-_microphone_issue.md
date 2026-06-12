---
title: "Speech recognition software - microphone issue"
date: 2014-04-06
forum: General Help
---

### Post by Tristan_Williams on 2014-04-06
I just downloaded the "Palaver" speech recognition software.
It works as it is supposed to so far, except I can't figure out how to make a mic work with it.

I have a USB RocbBand Mic from Xbox 360.

First of all, how do I get the mic to work on the computer, and second, how do I make it be recognized by the speech recognition software?

---

### Post by tgalati4 on 2014-04-06
Open a terminal and post the output of:

```
lsusb
```

---

### Post by Tristan_Williams on 2014-04-06
```

Bus 002 Device 025: ID 05ac:129e Apple, Inc. iPod Touch 4.Gen
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:0a03 Logitech, Inc. Logitech USB Microphone
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

