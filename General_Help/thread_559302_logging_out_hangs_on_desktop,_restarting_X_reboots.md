---
title: "logging out hangs on desktop, restarting X reboots"
date: 2007-09-25
forum: General Help
---

### Post by crazybilly on 2007-09-25
I recently tried installing a couple strange things, xcompmgr (did wierd things to my dialogs, but looked cool) and kwin on gnome (nice eyecandy, but a bit to system intensive).  I also have a smb share mounted on a local folder via cifs in fstab.

Now, unfortunately, I've got a bit of a problem:  I can't really logout.  Or restart X.

Here's what goes down:  when I logout via gnome's logout menu, the computer starts logging out.  the panels disappear as do the desktop icons.  But the desktop wallpaper stays up, as does the mouse cursor.  And then the computer stays there till I turn it off via the power switch.  Hitting ctrl+alt+backspace does nothing (as does any other keyboard combination, including ctrl+alt+any number or Fanynumber).

If, rather than logging out, from gnome, I hit ctrl+alt+backspace, X will usually restart normally once.  The next time I hit it, the computer will reboot, rather than restart.

I'd be happy to troubleshoot this, but since the problem is the locking up and the restarting, I don't really know where to look for logs or anything.

Anybody got any ideas of how I can go about figuring out what's going on?

Thanks!

---

### Post by crazybilly on 2007-09-25
update: the rebooting rather than restarting seems to be rather random--I can't get it to it do it right now.  Is it fixed? or am I just not triggering the bug?  No clue.  If I figure that part, I'll post.

also, note that this isn't the 'blank screen' bug--X is still running and the desktop wallpaper is still up.  And hibernation seems to work just fine, as does actually shutting down (althoguh it takes forever b/c the CIFS thing has to timeout....fixing that is next on the list)

thanks again.

---

### Post by crazybilly on 2007-09-25
another update:  logging out from a new user seems to be pretty normal--it's not borked.

also, the ctrl+alt+backspace thing is REALLY strange.  Sometimes it works, sometimes it shuts down or restarts the computer. Most recently, it hung at the (blank) desktop like when I log out.

I'm assuming there's a persistent log of what's going on behind the scenes somewhere.  Anybody know where it is? Or at least how to turn it on?

---

