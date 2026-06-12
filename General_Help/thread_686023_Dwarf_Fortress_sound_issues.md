---
title: "Dwarf Fortress sound issues"
date: 2008-02-02
forum: General Help
---

### Post by nunix on 2008-02-02
I'm not sure on the policy for thread necromancy; there's [this thread](http://ubuntuforums.org/showthread.php?t=533013) but it doesn't cover anything other than getting it running.

Note that I can play DF fine with no sound if I uncheck all the sound drivers in WINE. This is under 7.04 with WINE version 0.9.33

The trouble comes with getting sound to work. -.- This is running on a Pavillion dv4000, so it's using some onboard sound chip.

What'll happen if I get sound up - checking a driver, and then usually needing to enable Emulation hardware acceleration - is choppy, scratchy sound, and about a million feedback errors (the game continues to run) in the terminal window to the tune of:

fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=32768 < primary_done=40572)

The numbers are different on each line.

1) What's going on? Is it a memory issue, buggy code, or..?
2) Best chance at fixing it? (if I need to install a new version of WINE, what's the best way to go about that, re: uninstalling old version, where to get new version, so on)

---

