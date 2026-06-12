---
title: "Screen is mirrored after installing drivers"
date: 2014-12-23
forum: General Help
---

### Post by jose59 on 2014-12-23
I couldn't find anything about this.
Well after installing NVidia Drivers(my GPU is GeForce G105M) my screen looks like this(after reboot): [http://i.imgur.com/a9rTHOY.jpg](http://i.imgur.com/a9rTHOY.jpg)
Sorry for low res :/
To fix this i reverted to Xorg Server and went again to NVidia drivers, but noticed that games like cs1.6 and minecraft(with optifine, max frames cfg) had 20fps.
After typing ```
[FONT=Ubuntu Mono]lshw -c video[/FONT]
``` i got that i was actually using nouveau.
Reinstalled again Nvidia drivers and went to the same: [http://i.imgur.com/a9rTHOY.jpg](http://i.imgur.com/a9rTHOY.jpg)
If i try to use xrandr to set my screen res(i tried 1366x768 and 1368x768) it gives me an error.
Any help is appreciated, probably i will reinstall ubuntu but this time i won't install nvidia drivers.

---

