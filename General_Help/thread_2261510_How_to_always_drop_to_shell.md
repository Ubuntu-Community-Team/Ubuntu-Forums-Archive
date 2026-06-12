---
title: "How to always drop to shell?"
date: 2015-01-19
forum: General Help
---

### Post by ld.4lpha on 2015-01-19
Sometimes I will have an application or my desktop environment (it's happened with both Gnome and Cinnamon) go wonky and totally lock the system.  I will try to use keyboard shortcuts to pull up a terminal, run xkill, or anything else to try to recover, but often it requires that I pull the power cord.  I know the issue is with the desktop environment because I can see faults in the logs when I boot back up.

My question is this: how can I configure a keyboard shortcut that is managed/handled by the kernel and given a high priority so that when I execute it, the system simply kills the desktop environment and drops to shell?

Thanks for any thoughts!
LD

---

### Post by Holger_Gehrke on 2015-01-19
I don't think you need to configure anything. There are the virtual terminals that you can get to by hitting 'ctrl-alt-f1' to 'ctrl-alt-f6'. You can just log in on one of these and get a shell. 

If those don't work because the machine's to busy to even notice the keys, there's a trick with holding Alt-SysReq or AltGr-SysReq and typing certain letters: 'S' for sync (write all unwritten changes to disk), 'U' for unmount and remount read-only (all mounted disks) and 'B' for reBoot. Since 12.10 some of the other functions that used to be available in this way have been disabled for security reasons.

---

