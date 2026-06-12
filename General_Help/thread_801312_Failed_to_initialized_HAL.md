---
title: "Failed to initialized HAL"
date: 2008-05-20
forum: General Help
---

### Post by spid on 2008-05-20
I read a lot on this subject but no action fixed my problem. The problem occurred after an update (I don't remember which packages were involved but I think Nautilus was concerned).

Symptoms : system very slow on opening, mouse and screen freeze, no more suspend and hibernation. Problem recurrent. Same thing on different kernels (see below).

Work around : disconnect and reconnect (disconnection take at least 50 s)

Any idea would be appreciated.

Thanks

- Ubuntu 8.04 - Kernel 2.6.24-16-generic
- dbus ---> S12dbus hal--->S24hal
- .xsession-errors - some error messages (but I don't know if they are related to my problem):
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
** (nautilus:7440): WARNING **: Unable to add monitor: Non pris en charge
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000

---

### Post by housam on 2008-05-20
type in a terminal 
```

sudo apt-get install ubuntu-desktop
```
it may help

---

### Post by spid on 2008-05-20
Tried - to install ubuntu-desktop
      - to reinstall hal

but no change

---

### Post by spid on 2008-05-21
I think it has something to do with ati fglrx driver. Got rid of it and everything is back to normal even if it seems to me that it is a bit slower than before.

---

### Post by spid on 2008-05-24
It could help somebody. It had nothing to do with the ati fglrx driver. The problem appeared later. The problem is related to pulseaudio : remove it and that's all. Fixing pulseaudio setup would probably a more elegant solution but I made some readings on what it is supposed to do and I definitively don't need it. My system is ok now.

---

### Post by geekATlarge on 2008-05-25
Not sure it helps, but just fixed the HAL problem on my system. Look at: [Failed to initialized HAL, can't mount USB, log-out icon locks-ups]("http://http://ubuntuforums.org/showthread.php?t=806813")

---

