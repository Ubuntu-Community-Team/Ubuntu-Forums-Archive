---
title: "Massive CPU usage"
date: 2007-01-12
forum: General Help
---

### Post by zergberg on 2007-01-12
I've been having a problem recently where Xorg (or something) will magically jump to 100% CPU and effectively prevent anything from being accomplished. Also, there seems to be a lot of disk usage during this time, though I don't know which disk (given the noise I wager it's the older one) and whether it's reading or writing.

GNOME's System Monitor Panel Applet reports a lot of CPU usage in the I/O Wait category.

This problem happens with pretty much any combination of apps running, occurs in both GNOME and fluxbox. It's happened from actions ranging from applying filters in GIMP to loading Digg in Firefox to opening a video from Thunar (into several different media players.)

This is very annoying, since the only way to remedy it is often to kill X... Assuming the CPU isn't so overloaded that it can't read the Ctrl+Alt+BkSpc anymore...

Anyone know how to solve it?

---

### Post by BillGod on 2007-01-12
Not sure if this is your problem or not.  There is a known bug for this.  Here is the work around

[http://ubuntuforums.org/showpost.php?p=1747864&postcount=53](http://ubuntuforums.org/showpost.php?p=1747864&postcount=53)

---

### Post by zergberg on 2007-01-12
It's not Nautilus--hence why the same thing happens in fluxbox

---

