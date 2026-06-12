---
title: "Cannot increase maximum frequency on battery."
date: 2013-03-09
forum: General Help
---

### Post by icarus128 on 2013-03-09
I have a really annoying problem.  For some reason the maximum CPU frequency on my laptop while on battery is set to 1Ghz.  This makes it dog slow and basically unusable while unplugged.  So far I've tried:

- Installing and configuring laptop-mode-tools
- Installing and configuring cpufreqd
- Using cpufreq-set -c 0 -f 2.4ghz
- Installing the cpu frequency applet and clicking the 2.4ghz setting.
- sudo gconf-editor, I found somewhere that there are supposed to be settings in /apps/gnome-power-manager.  
  There are not, (there's not even an entry for gnome-power-manager) though the package is installed.

ACAICT it is not possible, on my machine, to change the maximum on battery cpu frequency.  Any ideas?

---

