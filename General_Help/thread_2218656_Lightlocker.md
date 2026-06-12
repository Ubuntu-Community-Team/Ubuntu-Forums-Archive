---
title: "Lightlocker"
date: 2014-04-21
forum: General Help
---

### Post by mechanic on 2014-04-21
What's this lightlocker doing for me? It's installed without explanation in 14.04 and I can't see any function that wasn't in xscreensaver. How do I set screensavers in Lightlocker or do I run both that and xscreensaver?

---

### Post by Toz on 2014-04-21
A decision was made by the developers of Xubuntu to use light-locker is the new screensaver program in 14.04. Light-locker is more integrated with lightdm and offers a user-switching capability, but does not currently provide for screensaver animations and does currently have one pretty nasty bug (blank screen on resume from lock on some systems).

You shouldn't run both together - they will conflict.

You can still use xscreensaver if you are used to it. Simply uninstall light-locker and install xscreensaver.

---

### Post by mechanic on 2014-04-21
> **Toz said:**
> A decision was made by the developers of Xubuntu to use light-locker is the new screensaver program in 14.04. Light-locker is more integrated with lightdm and offers a user-switching capability, but does not currently provide for screensaver animations and does currently have one pretty nasty bug (blank screen on resume from lock on some systems).

You shouldn't run both together - they will conflict.

You can still use xscreensaver if you are used to it. Simply uninstall light-locker and install xscreensaver.

I don't understand from your reply what the point of including it was - it seems to be less functional than xscreensaver, and than using the login screen to switch users (how many users actually work with many accounts on the same machine these days?) What problem was it supposed to solve?

That was really the point of my original post.

---

### Post by ccrs8 on 2014-04-21
I personally like light-locker a LOT better than xscreensaver.  My screensaver in 13.10 and earlier was always just a blank screen so the fact that light-locker can't give me flying gadgets and animated gizmos is OK with me.  And the fact that it is clearly tightly integrated with the rest of the Xubuntu theme instead of something that looks really 1980s and CLI-ish is quite nice.  The functionality is essentially the same, of course, but the polish is nice.  As for switching users, I run in to this situation on a weekly basis.  My primary workstation is also my wife's secondary workstation and she has an account on it.  If I'm downloading something, listening to something, etc., she just locks my session and logs in with her account when she needs to use it.  Not sure how common my use-case is, but we switch users quite a bit.

---

