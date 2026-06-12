---
title: "CD burning problems"
date: 2007-03-08
forum: General Help
---

### Post by M$LOL on 2007-03-08
This is what I get when I try to erase a CD-RW.
```
sudo brasero
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(brasero:5141): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
I/O warning : failed to load external entity "/root/.gnome2/brasero.session"

** (brasero:5141): CRITICAL **: nautilus_burn_drive_get_media_type: assertion `drive != NULL' failed

** (brasero:5141): WARNING **: No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/temp/152


** (brasero:5141): WARNING **: No property volume.disc.is_appendable on device with id /org/freedesktop/Hal/devices/temp/152


** (brasero:5141): WARNING **: the enable-monitor property is deprecated and will be removed in the next version

** (brasero:5141): WARNING **: Couldn't unmount volume in drive: /dev/scd0

```
Why isn't it working?

---

