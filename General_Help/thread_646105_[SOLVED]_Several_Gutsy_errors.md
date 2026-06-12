---
title: "[SOLVED] Several Gutsy errors"
date: 2007-12-20
forum: General Help
---

### Post by waldrepdebater on 2007-12-20
I've been using Ubuntu for 2 or 3 months now and have been absolutely loving it.  However, today when I booted it up I noticed that all of the hard-drive icons have disappeared from the desktop.  I never use them so I wasn't worried about it.  Then when I tried to connect to the internet the network-manager icon from the top toolbar is missing...I have no idea how to connect to the internet without this.  :)  Everything else appears to be fine at a glance...  In order to get on here I'm having to use my old Windows Vista, so I'd like to resolve this problem and get back to Linux as fast as possible.  Does anyone have any idea what is wrong?  It appears to just be a problem with the desktop icons...I would not know though...

---

### Post by Gen2ly on 2007-12-20
It's possible your icon cache has gone bad.  Occasionally this can become ... corrupt.  This can happen occasionally.  If this doesn't work, it might be necessary to remove the local (~/.icons) cache.  Try build it  the system wide one first:

> gtk-update-icon-cache -f /usr/share/icons/hicolor/

---

### Post by waldrepdebater on 2007-12-22
I entered that and got this response: ```
Failed to write cache file: Permission denied

```

On the bright side the network manager icon is back again.  All that seems to be missing is the hard drive icons.  I actually prefer not having those on my desktop.

---

### Post by markwren on 2007-12-23
> **waldrepdebater said:**
> I entered that and got this response: ```
Failed to write cache file: Permission denied

```

On the bright side the network manager icon is back again.  All that seems to be missing is the hard drive icons.  I actually prefer not having those on my desktop.

You need Superuser rights:
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

But it hasn't helped me!

Also run gconf-editor. Look for Apps/Nautilus/Desktop and check that your desktop icons are ticked. Mine are. And they still don't display. Same with or without the Compiz renderer.

My desktop icons disappeared after one of the last Ubuntu updates. There's now no right click menu on the desktop either. And Nautilus sometimes thrashes 99% cpu after I logout, and then I get a blank background when I login again - until I kill the nautilus process.

Something has screwed up in one of the last updates through the update manager! It's something in the last 4 weeks (the time since I last updated).

---

