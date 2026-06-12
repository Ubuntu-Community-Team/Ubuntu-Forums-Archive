---
title: "&quot;PS/2 Mouse&quot; on Laptop?"
date: 2008-01-12
forum: General Help
---

### Post by chrini on 2008-01-12
I recently posted a problem concerning the "joystick" in the middle of Latitude D610 keyboard. I have discovered that it's "Ubuntu Name" is "PS/2 Mouse" (I know this because I ran cat /proc/bus/input/devises and then cat /dev/input/mouse2; I ran it for all mouseX possibilities X=0..3 and it turned out to be the handler mouse 2).

Ok, so after that bit of information. I am now ready to comment it out of the xorg.conf file, but it isn't even in there.... How do I get this device to stop working if it isn't in the xorg.conf file? (In case you didn't see my other post, the "joystick" or "PS/2 mouse" is messed up and pulls my mouse pointer to the corner of the screen).

I appreciate all the help possible. Thanks.

---

