---
title: "VirtualBox segfault"
date: 2007-08-29
forum: General Help
---

### Post by Molerat on 2007-08-29
Recently, VirtualBox has become very unstable on my system.  I have tried to diagnose the problem as best I can, but I'm afraid I'm kind of stuck at this point.

I am running a standard VB install on Feisty, which ran flawlessly until about a week ago.  I believe, but cannot be certain, that the instability started after a round of updates from the package manager.  At first, VB would refuse to load altogether.  Sometimes it would make it as far as the initial VM chooser screen before completely freezing up.  From the command line:

```

$ VirtualBox 
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Segmentation fault (core dumped)

```

This looks like a Qt error to me, which reminded me of a recent update.  I checked Syntaptic and noticed the following log:

```

Commit Log for Sat Aug 25 09:53:57 2007

Upgraded the following packages:
kdebase-bin (4:3.5.6-0ubuntu20.1) to 4:3.5.6-0ubuntu20.2
kdebase-kio-plugins (4:3.5.6-0ubuntu20.1) to 4:3.5.6-0ubuntu20.2
kdelibs-data (4:3.5.6-0ubuntu14) to 4:3.5.6-0ubuntu14.1
kdelibs4c2a (4:3.5.6-0ubuntu14) to 4:3.5.6-0ubuntu14.1
kdesktop (4:3.5.6-0ubuntu20.1) to 4:3.5.6-0ubuntu20.2
libkonq4 (4:3.5.6-0ubuntu20.1) to 4:3.5.6-0ubuntu20.2

```

It appears that I chose to upgrade a few KDE libraries that were recommended by the Update Manager on Saturday.  I run Gnome, so I assume these are VB dependencies.  I thought I would try to downgrade by forcing an older version.  So I manually rolled back the updates to the older version.  After this I found I could run VB maybe 50% of the time.  I still hit stretches where it will segfault and die.  I am not sure what else to try.  Does anyone have any recommendations?

---

### Post by Molerat on 2007-09-04
In case anyone comes across this thread in the future, it appears that VirtualBox has been updated to fix whatever was causing the problem...

---

