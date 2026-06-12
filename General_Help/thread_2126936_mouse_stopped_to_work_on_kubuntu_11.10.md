---
title: "mouse stopped to work on kubuntu 11.10"
date: 2013-03-18
forum: General Help
---

### Post by tkoomzaaskz on 2013-03-18
[COLOR=#000000][FONT=Arial]I have kubuntu 11.10 (oneiric ocelot). Few days ago I ran sudo apt-get upgrade and after restart my USB mouse stopped to work. When the kde login screen is displayed, I cannot move the cursor with the mouse, but I can move it with my touchpad (thanks God). The electricity is ok with the USB, because the diodes are lit. When I put a pendrive, it works fine.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When I have the mouse plugged and I run lsusb, it prints:[/FONT][/COLOR]

```

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 04f2:b105 Chicony Electronics Co., Ltd 

```[COLOR=#000000][FONT=Arial]
My dmesg output goes like the following:[/FONT][/COLOR]

```

[ 1679.516186] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[ 1679.756167] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 1680.212095] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 1680.408140] hub 8-0:1.0: unable to enumerate USB device on port 1
[ 1682.328182] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[ 1682.568190] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 1684.876147] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[ 1685.116168] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 1685.368195] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 1685.564208] hub 8-0:1.0: unable to enumerate USB device on port 1
[ 1687.484128] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[ 1687.724163] hub 2-0:1.0: unable to enumerate USB device on port 3

```[COLOR=#000000][FONT=Arial]

...but I don't know how to interpret it. I tested this mouse on another computer (with Windows) and it worked, so the mouse itself is ok. I guess it has something to do with drivers that could have been installed improperly, but I'm really weak in hardware stuff. Please give me a hint what should I check.[/FONT][/COLOR]

---

### Post by varunendra on 2013-03-18
Did you try connecting it to a different port?

Please post output of -
```
xinput
usb-devices | grep -iA6 -B2 b105
lsmod
dmesg | grep -i usb | tail -20
```

---

