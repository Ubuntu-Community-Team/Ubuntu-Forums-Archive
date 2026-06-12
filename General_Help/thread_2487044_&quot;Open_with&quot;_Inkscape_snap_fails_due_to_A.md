---
title: "&quot;Open with&quot; Inkscape snap fails due to AppArmor"
date: 2023-05-21
forum: General Help
---

### Post by enricobe on 2023-05-21
Hello I can't open any .svg file with Inkscape on Kubuntu. Inkscape is installed as Snap.

Journalctl returns this

```

mag 21 18:11:38 enrico-kubuntu plasmashell[114946]: ink_file_open: '/home/enrico/Desktop/orto.svg' cannot be opened!
mag 21 18:11:38 enrico-kubuntu plasmashell[114946]: InkscapeApplication::document_open: Failed to open: /home/enrico/Desktop/orto.svg
mag 21 18:11:38 enrico-kubuntu plasmashell[114946]: ConcreteInkscapeApplication::on_open: failed to create document!
mag 21 18:11:38 enrico-kubuntu kernel: audit: type=1400 audit(1684685498.745:2238): apparmor="DENIED" operation="open" class="file" profile="snap.inkscape.inkscape" name="/home/enrico/Desktop/orto.svg" pid=114946 comm="inkscape" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
mag 21 18:11:38 enrico-kubuntu kernel: audit: type=1400 audit(1684685498.745:2239): apparmor="DENIED" operation="open" class="file" profile="snap.inkscape.inkscape" name="/home/enrico/Desktop/orto.svg" pid=114946 comm="inkscape" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
mag 21 18:11:38 enrico-kubuntu kwin_x11[2450]: qt.qpa.xcb: QXcbConnection: XCB error: 3 (BadWindow), sequence: 47901, resource id: 25167136, major code: 18 (ChangeProperty), minor code: 0
```

How can I fix this issue?
I have to open Inkscape and then use the "Open" menu within the application. Everything works fine when using the app, the error is related to the "double click" open

---

### Post by #&amp;thj^% on 2023-05-21
See if these are installed:
```
xdg-desktop-portal-kde
xdg-desktop-portal-gtk
```
I'm one who won't use snaps currently.

It's also is available in Flatpak:
```

Inkscape permissions:
    ipc                   network               wayland       x11
    file access [1]       dbus access [2]

    [1] host, xdg-config/gtk-3.0, xdg-run/gvfs, xdg-run/gvfsd
    [2] org.gtk.vfs.*
```

---

### Post by enricobe on 2023-05-21
Hello, the 2 packages are correctly installed. Everything works fine when opening files and this kind of actions, but it seems to be an AppArmor "problem" IMHO.
I know it's available in flatpak, but I'm trying the "ubuntu experience" using snaps packages :-)

---

### Post by #&amp;thj^% on 2023-05-21
> **enricobe said:**
>  but I'm trying the "ubuntu experience" using snaps packages :-)

Enjoy :) That experience is not a repeat of what I'm after. :)

---

