---
title: "apt-get dist-upgrade killed system"
date: 2006-12-27
forum: General Help
---

### Post by android6011 on 2006-12-27
I had feisty all installed, then I wanted to do an update so i apt-get update && apt-get dist-upgrade, after reboot it goes to grub screen then I get this:

Loading, please wait... (sits there for a few minutes)
        Checking root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/3a459f1c-241b-40ea-abd7-488c1bf78eb does not exist
dropping to a shell!

then busybox shell is below that. not sure what went bad here. any help would be great.

---

### Post by taurus on 2006-12-27
Instead of using UUID in /etc/fstab for your /, you need to go back to the old fashion and use the /dev/hda1 (or whatever the partition / is resided)...

---

### Post by d3v1ant_0n3 on 2006-12-27
See [ here](http://ubuntuforums.org/showthread.php?t=322885) at a guess.

I dropped out of Feisty after the last round of breakage. I'll be back later:D  Much as I love the breakage and randomness (it helps me learn) I'd actually like to be able to boot my system now and again. There's some pretty big changes this time round, I'd expect more major breaking along the line for a while yet- remember, it's still 4 months away from release on a 6 month release schedule.

---

