---
title: "Computer won't boot after update"
date: 2007-04-23
forum: General Help
---

### Post by BreakDecks on 2007-04-23
I was updating from 6.06 to 6.10, planning to update to 7.04 after that, but after installing 6.10, my computer won't boot.  I left it running overnight, and around midnight it said 2.5 hours remaining.  At 5 AM, I got on and checked to see if it was done, but Xscreensaver wouldn't accept my password to get back to my desktop.  I did Ctrl+Alt+F2 and killed Xscreensaver, but this caused Xorg to crash.  After that, Xorg wouldn't start back up again, so I assumed that that I just needed to reboot my computer to finish the update, but now after mounting the root file system, the screen just goes black.  If I have any USB drive attached, it gives the the "cannot accept request" error (or something of that sort, I am not near the problem computer atm).

I really need to get my computer back up and running again, and I was wondering how I either go back to 6.06 or fix whatever is wrong with my newly updated 6.10 installation.

My best guess as to what may have gone wrong is that edgy may not have finished installing (the 2.5 hour remaining time estimate may have been completely wrong), but I was unable to see this due to Xscreensaver.

---

### Post by BreakDecks on 2007-04-23
bump

I really need to fix this.

---

### Post by bg1256 on 2007-04-23
Boot into the recovery mode, log in and try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

