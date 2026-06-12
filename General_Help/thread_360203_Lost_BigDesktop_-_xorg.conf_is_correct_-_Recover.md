---
title: "Lost BigDesktop - xorg.conf is correct - Recover?"
date: 2007-02-12
forum: General Help
---

### Post by madcow72 on 2007-02-12
Hello!

I was playing with beryl and couldn't get it to work with bigdesktop mode on my machine, (P4 2.4GHz, Radeon 9250 128MB, Ubuntu 6.10, dual 19"flatpanel) so I created two alternate xorg.conf files to either:  1)  clone my desktop onto each monitor or 2)  Use the dual-head system so that individual desktop environments work on each monitor.  Good news is, I got beryl working.  Bad news is, when trying to go back to bigdesktop, the system always returns to clone mode.

When at the login screen, I actually have bigdesktop working across both monitors, but after logging in, it switches back to clone.  I tried creating another user to test it out, and realized that the other user is able to use bigdesktop with no problem.  I then tried copying the .gconf, .gconfd, .gnome, .gnome2, and .gnome2_private hidden files from the new user's /home/newusr/ directory into mine - but nothing changes.  This problem is user specific and probably very easy to fix, but unfortunately it's still beyond me!  Any suggestions?  Gracias!!

---

### Post by madcow72 on 2007-02-13
Ba-bump!

I know it's stupid, but I'm about to re-install (and upgrade to Feisty) if no one can offer any suggestions!?

---

### Post by s0urce on 2007-03-11
Man oh man, I've got the same exact problem. Big-Desktop works fine on the login screen yet when I get into Gnome it turns into Clone Mode. Nothing I do seems to work. I've reinstalled 3 times now and followed the guides to the T.

---

### Post by redwheelbarrow on 2007-04-08
> **madcow72 said:**
> Hello!

I was playing with beryl and couldn't get it to work with bigdesktop mode on my machine, (P4 2.4GHz, Radeon 9250 128MB, Ubuntu 6.10, dual 19"flatpanel) so I created two alternate xorg.conf files to either:  1)  clone my desktop onto each monitor or 2)  Use the dual-head system so that individual desktop environments work on each monitor.  Good news is, I got beryl working.  Bad news is, when trying to go back to bigdesktop, the system always returns to clone mode.

When at the login screen, I actually have bigdesktop working across both monitors, but after logging in, it switches back to clone.  I tried creating another user to test it out, and realized that the other user is able to use bigdesktop with no problem.  I then tried copying the .gconf, .gconfd, .gnome, .gnome2, and .gnome2_private hidden files from the new user's /home/newusr/ directory into mine - but nothing changes.  This problem is user specific and probably very easy to fix, but unfortunately it's still beyond me!  Any suggestions?  Gracias!!

Could you post the output of xrandr please. It could be as easy as changing your screen size...

---

### Post by madcow72 on 2007-05-07
Just noticed your reply to this thread, redwheelbarrow.  Fortunately, I gave up on ATI and changed to a NVidia card, also upgraded to Feisty.  Life with NVidia is sooo much better than life with ATI and this problem has actually been solved for quite some time.  Thanks for your post, though!

---

