---
title: "After power loss, graphics issue after login, failsafe GNOME works fine"
date: 2008-06-10
forum: General Help
---

### Post by painaxl on 2008-06-10
I'm running Hardy on an older emachines 1ghz intel with onboard video (don't have the exact chipset on hand).  Was running Feisty up until last weekend when I did a clean install.  Hardy was working fine up until we lost power last night (two days after the install).

The computer now boots up fine to the login screen.  After logging in, however, the screen resizes while the intro sound plays.  Then it changes again and becomes a jumbled jigsaw version of the desktop with horizontal lines across it.  You can't move the cursor or see anything beyond the pattern.  Pressing CTRL-ALT-BACKSPACE goes right to the blank desktop (the default background with the bird which looks perfect) before returning me to the login screen.  Logging into "failsafe GNOME" works just fine and doesn't have any of the graphics issues.

I've tried dpkg -a configure as well as reconfiguring xorg.  Any idea on where else to start troubleshooting this problem or what might have caused it?

Thanks!

---

### Post by painaxl on 2008-06-19
BUMP.  Still having this problem.  Anyone else have this or know how I should start troubleshooting?

---

### Post by gincognito on 2008-06-20
I got a similar, but different :), issue 2 nights ago. The desktop was running fine at 1080i while watching a few .avi's. The update icon was on the screen (Ubuntu 8.04 64 bit, nvidia 7600) so I installed the 60+ updates. It required a restart which I figured I would do when I called it a night. When I tried to shutdown, it froze. So I did a big no-no and just shut it down (same effect as power loss). Upon restart, it goes into failsafe mode. I tried a proper shutdown and still failsafe. I looked at my Xorg.conf file and it looks good. I looked into the Xorg.0.log file and the failsafe comment is pretty much at the top of the file. I haven't figured it out yet.

It's not as nice watching stuff at 800x600 instead of 1080i :(

---

