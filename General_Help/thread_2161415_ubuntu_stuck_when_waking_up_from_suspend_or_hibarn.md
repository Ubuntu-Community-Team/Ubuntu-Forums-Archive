---
title: "ubuntu stuck when waking up from suspend or hibarnate"
date: 2013-07-10
forum: General Help
---

### Post by michaelbr92 on 2013-07-10
ubuntu using gnome 3.8 wont wake up from suspend/hibarnnte and show only the desktop wallpaper

---

### Post by KeepItSimpleStupid on 2013-07-10
Had a similar issue.  Can you get to the terminal?   CNTROL+ALT+t  I think I was able to reset the trackpad/mouse.

---

### Post by Nixarter on 2013-07-10
This may be part of a known issue (not really a "bug").  Whenever installing from wubi, the entire OS is in a file, not a partition.  Therefore, when rtying to recover from hibernation or whatnot, the hibernation file is not in a file on the partition... it is in a file inside your ubuntu.disk file, which is in the partition.  It doesn't check there, and therefore cannot find it and freezes.  Wubi was meant to be a way to test out the OS.  it is not meant to be a permanent install solution.

---

