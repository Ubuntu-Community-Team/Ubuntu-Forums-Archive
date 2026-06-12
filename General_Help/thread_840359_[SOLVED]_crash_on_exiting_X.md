---
title: "[SOLVED] crash on exiting X"
date: 2008-06-25
forum: General Help
---

### Post by dracayr on 2008-06-25
hi,

when I kill X, I almost always get a black screen (on logging off, switching to a tty, sudo pkill X, shutting down the system, etc..) . the computer is still on, but the keyboard doesn't respond (no Sysrq). All that I can do is shut the computer off physically :(. I don't think it has anything to do with my wm, because it's the same under gnome and e17. I looked in my xorg.0.conf, but didn't find anything special (but then, I don't know for what to look)

```
dracayr@dracayr@dracayr-lab:~$ grep EE /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
dracayr-lab:~$ grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000
9
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
(WW) intel(0): Allocation error, framebuffer compression disabled
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
(WW) intel(0): EXA greedy migration mode enabled.
(WW) intel(0): Chosen PLL clock of 66.6 Mhz more than 2% away from desired 65.1 
Mhz
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) Configured Mouse: No Device specified, looking for one...
dracayr@dracayr-lab:~$ grep NI /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
dracayr@dracayr-lab:~$ grep "??" /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
dracayr@dracayr-lab:~$
```


EDIT: I added 
Option "XAANoOffscreenPixmaps" "true"

to my xorg.conf, rebooted, and now I switched about 7 times from tty to X without crash (I hope it's no coincidence). I'm sorry that I posted this thread and found the solution myself so fast, but that was coincidence. I had this problem for over half a Year now...

dracayr

---

