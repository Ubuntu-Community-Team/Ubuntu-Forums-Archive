---
title: "snap: after revert, provider libraries looked for in folder of newer snap version"
date: 2022-06-13
forum: General Help
---

### Post by geestbos on 2022-06-13
A snap (whatsdesk) suddenly stopped working, complaining of a missing library, and I tried reverting it (from version 28 tot version 25), at the same time also reverting the provider snaps  (gtk-common-themes and gnome-3-28-1804).

Now whatsdesk still fails, but differently. It cannot load an (Gtk-common-themes provided) icon, because the (gnome-3-28-1804 provided) icon loading module is not found. The strange thing: it looks for the icon in the correct folder of version 25 of whatsdesk, but for the icon loading module in the wrong folder of version 28 of whatsdesk:

```
Failed to load /snap/whatsdesk/25/data-dir/icons/Adwaita/16x16/status/image-missing.png: Unable to load image-loading module: /snap/whatsdesk/28/gnome-platform/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so

```

Any advice?

---

### Post by geestbos on 2022-06-13
Ok, found it, the file gdk-pixbuf-loaders.cache inside ~/snap/whatsdesk/common/.cache still contained references to version 28. Changing the file manually as to point to version 25 solved the issue.

---

