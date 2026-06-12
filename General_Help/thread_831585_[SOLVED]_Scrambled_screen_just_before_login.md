---
title: "[SOLVED] Scrambled screen just before login"
date: 2008-06-17
forum: General Help
---

### Post by siddartha on 2008-06-17
Been using an workstation which has been idle for over an year. Did each distro upgrade as Ubuntu isn't smart enough to spare the servers the intermediate steps. No problem beyond the lost time.

Than did an upgrade from 1G to 2G RAM. Now the problem starts. It is a nfoce with integrated gpu and an am2 athlon. Starting in troubleshoot mode and than starting by hand the processes in runlevel 5 leads to a working computer. Letting everything go auto means that everything will load up until a few microseconds before starting the log in screen. At that point there would be garbage on screen and not just any garbage - constantinly moving garbage. After that the computer is unusable.

What could solve the problem?

Cheers,
Sidd

---

### Post by Lord Xeb on 2008-06-17
Sorry that I cannot help but that does sound interesting.

---

### Post by siddartha on 2008-06-17
As usual, the community is not very helpful, but by the power of google the answer is this:
- upgrade to the newest nvidia-glx-new
- upgrade to the newest bios, by making a CD/floppy with freedos
Now it works like a charm.

---

