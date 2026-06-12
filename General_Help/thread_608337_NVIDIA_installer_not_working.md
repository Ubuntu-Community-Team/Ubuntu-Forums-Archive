---
title: "NVIDIA installer not working"
date: 2007-11-09
forum: General Help
---

### Post by noahw on 2007-11-09
I had gutsy running fine on the nvidia-glx package, but I installed the driver from nvidia's website and now it's having trouble with the drivers.  The computer goes into terminal in startup, the screen flashes several times and then a window pops up telling me it could not completely detect the video card and monitor, with the option to configure it.  When I configure it, it says that the driver is something called 'vesa'.  I change it to 'nv' and then boot the computer.  It starts up fine but in low resolution.  When I check what driver it is using after it boots up, it's switched back to 'vesa'!

Please help :(.

---

### Post by noahw on 2007-11-10
By the way, I tried editing xorg.conf and it still switches drivers.

---

### Post by FuturePilot on 2007-11-10
Did you purge the driver you installed through the repos? Chances are if you didn't remove that one you're getting conflicts because it's trying to load two different versions at once.

---

### Post by noahw on 2007-11-10
nvidia-glx?  I tried booting both with that and without, same results.

---

### Post by noahw on 2007-11-17
bump

---

