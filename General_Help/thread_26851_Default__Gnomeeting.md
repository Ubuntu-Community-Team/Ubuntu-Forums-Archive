---
title: "Default  Gnomeeting"
date: 2005-04-14
forum: General Help
---

### Post by rosagonzpe on 2005-04-14
Thanks before hand.
My problem is as follows:
I have a quickcam zoom usb, and works. But Gnomeeting has as only option V4l2 and mine works only under V4l.
How can I make Gnomeeting works under V4l and not V4l2, because it gives the error:

* error when opening /dev/video0 *

Using V4l2.

But camorama, for example works, because uses V4l.
Any help???
Thank you

---

### Post by Bob D. on 2005-04-15
I'd suggest dropping a note to the GnomeMeeting user-mail list. Your question might be a bit too obscure for the folks in these forums, me included.  ;-)

Do post back to this thread what you get for the answer. That way we all can learn from your experience.

The GnomeMeeting user-mail list is here: [http://mail.gnome.org/mailman/listinfo/gnomemeeting-list](http://mail.gnome.org/mailman/listinfo/gnomemeeting-list)

Bob

---

### Post by hobnob on 2005-04-24
You need to install the PWLib video plugin for v4l and then select 'v4l' when setting up GnomeMeeting.
```
$ sudo apt-get install libpt-plugins-v4l
```

---

