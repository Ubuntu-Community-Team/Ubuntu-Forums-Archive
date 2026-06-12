---
title: "Startup fsck and beryl"
date: 2007-05-08
forum: General Help
---

### Post by z987k on 2007-05-08
I have 3 problems right now, all developed well after I installed, but I haven't done a damn think to bork the system.

First, at startup, every single time I start fsck wants to check sda1.  And every time it takes ~ 1/2 and hour to check the 40gb drive.  It says that it's been 30+n times since it's been checked even though it just was last boot.  I really need to find a way to stop that.  For right now I've just commented out sda1's line in fstab, then I mount it manually when the system is up - no problems.

Next beryl just suddenly stopped working for no reason.  I went to bed with the computer & beryl on, I wake up and there's the nice brown theme that is ubuntu's default.  I try to restart beryl but no luck... the little diamond is in the corner but no beryl or emerald for that matter.  What gives there?

---

### Post by LuisGMarine on 2007-05-08
For beryl:

The problem that you are having could be that beryl just crashed and reset itself to the default window manager.  Since beryl is BETA, keep in mind, things like this are going to happen a lot.  However its quite simple and easy to fix.  Try this:

**[SIZE="2"]Right-Click on the red diamond > Select Window Manager > Beryl[/SIZE]**

*[SIZE="1"]Note: If beryl wasn't already selected in the list, that shows you that there was probably a crash and beryl reset itself to the default window manager, which in this case is Metacy.[/SIZE]*

This next step is to make sure you have the emerald window decorator:

[SIZE="2"]**Right-Click on the red diamond > Select Window Decorator > Standard Beryl Decorator(emerald)**[/SIZE]
[I][SIZE="1"]
Note: Once again , this could have been set to something else if it indeed crashed.  This should have gotten your beryl to work again, if it doesn't do a quick X restart and try it again.[/SIZE][/I]

Good Luck, Hope this helps!

---

### Post by mcduck on 2007-05-08
> **z987k said:**
> I have 3 problems right now, all developed well after I installed, but I haven't done a damn think to bork the system.

First, at startup, every single time I start fsck wants to check sda1.  And every time it takes ~ 1/2 and hour to check the 40gb drive.  It says that it's been 30+n times since it's been checked even though it just was last boot.  I really need to find a way to stop that.  For right now I've just commented out sda1's line in fstab, then I mount it manually when the system is up - no problems.


Let me guess, sda1 is either FAT32 or NTFS partition? In that case change the last number in it's entry line in fstab to '0' to disable fsck on that partition. That should fix your problem.

---

### Post by psusi on 2007-05-08
Does the fsck report any errors?  Assuming this isn't fat or ntfs like the above poster mentioned, try manually fscking it.  With it unmounted, do sudo fsck -f /dev/sda1.

---

### Post by z987k on 2007-05-08
The select window manager thing did it, don't know why I didn't check for that.

No the filesystem is an ext3 fs.  I am running fsck right now manually to see if anything comes up, but normally it doesn't when it automatically checks.

---

