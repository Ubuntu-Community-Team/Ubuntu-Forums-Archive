---
title: "kaffeine broken"
date: 2007-01-28
forum: General Help
---

### Post by kodoku on 2007-01-28
Hello all,

I've recently reinstalled a fresh edgy and everything was perfect.  Kaffeine worked beautifully along with many of the other applications.  After a week, however, kaffeine stopped starting up.  The bouncing icon would hang for a bit before disappearing with nothing happening.  I've repeatedly checked for extra instances of kaffeine and used killall, no help.  Running from konsole, I'd get this message:

X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/dev/dvb/adapter0/frontend0 : : No such file or directory
QLayout "unnamed" added to QWidget "unnamed", which already has a layout

With this, kaffeine will appear in the process tree, but the GUI never appears.  I've tried reinstalling kaffeine (I wanted to remove it, and then fresh install it, but synaptic/aptitude would remove kubuntu-desktop along with it, and I wasn't sure I wanted to do that), still no go.  I've even tried running it from the root konsole.

After digging deeper around the web, I read something about SCIM conflicting with kde apps (scim seems to break a lot of things..).  So I removed scim/skim and all of its related files, rebooted, and tried to start kaffeine from konsole again.  This time, this message appears:

X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/dev/dvb/adapter0/frontend0 : : No such file or directory
QInputContext: no input method context available
QInputContext: no input method context available
QLayout "unnamed" added to QWidget "unnamed", which already has a layout

Kaffeine's UI partially starts, I can see outlines of the window and blocks, and it hangs indefinately.  I always have to terminate it.

[[IMG]http://img254.imageshack.us/img254/4586/snapshot1hh5.th.png[/IMG]](http://img254.imageshack.us/my.php?image=snapshot1hh5.png)

I'm all out of ideas.  I don't HAVE to have kaffeine, but it's the best that I've used so far in terms of versatility and appearance.  

Help would be greatly appreciated!

---

### Post by david_2001 on 2007-01-28
Curious.  The first console message you quote is normal.  At least, it was normal before the recent update to KDE 3.5.6, after which the two BadDevice errors went away.

I wouldn't worry about uninstalling kubuntu-desktop.  It's essentially just a list of applications and dependencies that make up kubuntu, so nothing else will be removed with it and it can be reinstalled after you've completely uninstalled kaffeine.
> **Kubuntu desktop system**
This package depends on all of the packages in the Kubuntu desktop system

It is safe to remove this package if some of the desktop system packages are
not desired.

You can reinstall scim and whatever else you removed as well - I use kaffeine all the time without problems and with scim installed.  However, one thing I would do before trying to start kaffeine up again is delete all of its local settings files:
```
rm /home/<username>/.kde/share/config/kaffeinerc
rm -rf /home/<username>/.kde/share/apps/kaffeine
```

---

### Post by kodoku on 2007-01-28
actually, I had thought about kaffeine's config files, though I had no idea where to look.  I ended up completely removing kaffeine with aptitude, and then compiled and installed the latest version of kaffeine from source.  It started up fine after that.

Thanks for the reply though! I'll know where to look for kaffeine config files next time.

---

### Post by kodoku on 2007-01-28
ugh, nevermind

The new version crashes nonstop and sound is barely audible..

I'm back to square one.  I tried removing the files like you said, and kaffeine's installation check pops up no problem.  But afterwards, kaffeine hangs again like before.

I'm stumped.

---

### Post by david_2001 on 2007-01-28
Just a thought, do you have either xine or gxine installed and do they work ok?  Otherwise, you may want to try (a) going back through the last changes you made to your system before kaffeine stopped working the first time and (b) using strace to see what kaffeine is trying to do when it hangs up.

---

