---
title: "disable pop-up status messages?"
date: 2008-05-04
forum: General Help
---

### Post by jamvegan on 2008-05-04
Can anyone tell me how to disable the Windows-like status messages that pop up to tell me things like "You are now connected to Access Point X" or "Updates are available. Click the icon..."?

These are always, as far as I can recall, associated with the appearance of, or change to, an icon at the top of the screen--which is all the notice I need.  I find it irritating to have to either click the little box to make them go away, or have them hang around for a while, potentially blocking what I want to look at.

Oddly enough, the reason that I use GNU/Linux is *not* that I love Windows.  Please tell me how to go back to a quieter, non-redundant Gnome experience.  (Oh, yeah.  Feisty Fawn/Gnome, if that makes a difference.)

---

### Post by sdennie on 2008-05-05
Those popups come from the notification daemon.  I think that just killing that process will probably do what you want but, I don't know if it will have any other adverse effects.  So:

```

pkill notification-daemon

```

Also, it looks like it may be autostarted with dbus via the file /usr/share/dbus-1/services/org.freedesktop.Notifications.service.  Removing that file from that directory should stop the notification-daemon from ever being start I believe.

---

### Post by gsmanners on 2008-05-05
Or do this:

sudo chmod -x /usr/lib/notification-daemon/notification-daemon

---

### Post by jamvegan on 2008-05-06
Thanks vor and gsmanners.  I killed the process and chmoded the file, and am back to the blissfully "quiet" GNU/Linux experience I know and love. :-)

---

