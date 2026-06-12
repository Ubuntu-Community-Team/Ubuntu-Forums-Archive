---
title: "sensors-applet - no icons"
date: 2007-06-16
forum: General Help
---

### Post by _simon_ on 2007-06-16
screenshot says it all really.

Any ideas?

---

### Post by _simon_ on 2007-06-16
Fixed.

Had to run

```

sudo gtk-update-icon-cache -f -t /usr/share/icons/hicolor

```

Then remove and add the applet again to the panel.

---

### Post by MoLE on 2007-07-01
Thanks Simon - i was really struggling with this one.  i did find another workaround:
copy the contents of /usr/share/icons/hicolor/22x22/devices to  ~/.icons/hicolor/22x22/devices.

But this is a user-specific kludge.  I thought it might have something to do with updating the icon cache, but I couldn't find any documentation on how it worked.

---

