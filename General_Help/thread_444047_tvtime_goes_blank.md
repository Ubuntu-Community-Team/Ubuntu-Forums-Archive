---
title: "tvtime goes blank"
date: 2007-05-15
forum: General Help
---

### Post by CocoAUS on 2007-05-15
It seems to be rather random, though related to high cpu usage, but tvtime sometimes simply stalls.  The sound continues, but the screen freezes.  If I restart tvtime, it takes a moment to startup, and the screen is blue, though the sound continues.  It's also extremely slow switching channels (they're all blue anyway).  This is the ONLY reason I have to reboot my Ubuntu install.  Any ideas what's causing this, or how to fix it without rebooting?  Thanks.

---

### Post by fragos on 2007-05-15
Tell us more, CPU model, memory size, TV card or TV USB dongle.

---

### Post by CocoAUS on 2007-05-16
Pentium 4 3.0GHz with hyperthreading, ATi tvwonder card (uses the v4l driver, works out of the box), 1.5 gigs of RAM.  It happens regardless of what video driver I use (nv or nvidia).  It also freezes on Windows using the official ATi multimedia center software, but closing the viewer and reopening fixes it in Windows.

---

### Post by fragos on 2007-05-16
Almost sounds like driver driver/firmware problem.  Based on what you say the card has a role in this problem.  I've never used this card.  In a terminal window run "lsmod |grep videodev" so I can see what driver is used.  There may be a way to efectively reset the card that doesn't require a reboot.  Blue screen is a symptom of no signal or a misconfigured tuner and posibly other things.

---

### Post by CocoAUS on 2007-05-16
```
videodev               28160  3 cx8800,cx88xx
v4l2_common            25216  3 tuner,cx8800,videodev
v4l1_compat            15236  2 cx8800,videodev

```

---

