---
title: "Xubuntu 6.10 Sound Gone"
date: 2006-10-29
forum: General Help
---

### Post by Cable on 2006-10-29
Well, I installed Xubuntu 6.10, and sound *was* working.  Now, it has stopped for some reason.  I don't know if I did something or what.  Following is the output I believe would be useful...
```

user@user:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Riptide [Riptide], device 0: RIPTIDE [RIPTIDE]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

```
and
```

00:0c.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
        Subsystem: Risq Modular Systems, Inc. Riptide PCI Audio Controller
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 1080 [size=64]
        Capabilities: <access denied>

```
Any suggestions?  I'd really like to get sound back.  :-(

---

### Post by se7en on 2006-11-11
I had the same issue. It turns out my wave volume was reset and turned down to mute for some reason. I fixed it by loading the Volume Control applet into my panel and turning up the wave volume on the default device. I hope this helps you.

---

