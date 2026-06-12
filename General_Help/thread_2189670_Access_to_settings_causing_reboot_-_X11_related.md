---
title: "Access to settings causing reboot - X11 related"
date: 2013-11-23
forum: General Help
---

### Post by eric.hudish on 2013-11-23
Hello all,

Adding an issue I just worked around.

I just upgraded to 13.10, haven't been in Ubuntu for a while but just moved (physically) and upgraded my desktop after unpacking. After some issues with install (ie: the mouse/keyboard would not work, had to enable upgrade/package downloads during install process) Ubuntu seemed to work well enough. However, when I went to try and access system settings (via gui...never really tried cmdline) the system would reboot...constantly. There was nothing helpful in /var/logs really and I was having a heck of a time figuring out what was going on. This would occur in both Unity and Gnome.

As it turned out, my X11 xorg.conf was obliterated at some point, and attempts to run dpkg-reconfigure would NOT produce an xorg.conf file to put in place. If I find a reason to this, I'll try to post that answer later.

In any event, I wrote out an X11 xorg.conf manually and voila, no more reboots. I find this somewhat curious; I ***assume*** Ubuntu creates an xorg.conf on the fly during boot but then doesn't save it? I could have sworn in older versions if you deleted/moved the xorg.conf Ubuntu to create a new default version on boot and save the default in place for you...and why isn't dpkg-reconfigure creating a sample xorg.conf?

I haven't found any references to this type of bug in the first few pages here but I wanted to put my experience down for others. I guess the only questions left to answer are why is a default xorg.conf not being saved, and why does my dpkg-reconfigure not produce a sample xorg.conf? These two questions are probably related and/or one-in-the-same problem. 

Cheers-
TwistD

-- Update --

While I had some success it did reboot again a little while later. Had to change my drivers around and all seems 100% better now. Seems X11 doesn't fail nicely in the latest 13.10 which can cause issues for someone like me who mainly works in RHEL and is used to fidgeting with xorg.conf on a regular basis.

---

