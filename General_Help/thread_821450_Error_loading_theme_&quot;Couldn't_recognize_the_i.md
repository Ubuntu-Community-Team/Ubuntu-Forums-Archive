---
title: "Error loading theme: &quot;Couldn't recognize the image file format&quot;"
date: 2008-06-07
forum: General Help
---

### Post by kuio on 2008-06-07
Hi Ubuntu community, I need help!

Last night I shut down my system while firefox was not responding and today, while starting up again, I get error messages while loading the Human theme. They are the same kind of the following, which I get when I start firefox through the terminal:

```
(firefox:8036): Gtk-WARNING **: Error loading theme icon 'gtk-close' for stock:
Couldn't recognize the image file format for file '/usr/share/icons/gnome/16x16/actions/gtk-close.png'
```

So now my desktop has no toolbars at all and all the icons were replaced by this standard "sheet of paper" icon. When I double click this image file on my desktop, I get a pop up:

```
Could not load image 'ggg.jpg'. Unrecognized image file format
```

Firefox and Nautilus' buttons were replaced by "missing image" icons.

On Nautilus I get no response when I double click any music or video files.

I'm using an old Vaio laptop model PCG-GRT230 and i386/32 installation of ubuntu, and I run all updates available daily.

Does anyone have an idea of what this could be?

---

### Post by ChameleonDave on 2008-06-07
Something has got corrupted.

Try to start again with a clean profile.

---

### Post by kuio on 2008-06-07
> **ChameleonDave said:**
> Something has got corrupted.

Try to start again with a clean profile.

You mean to create a new user profile and try to log in again?

---

### Post by ChameleonDave on 2008-06-07
> **kuio said:**
> You mean to create a new user profile and try to log in again?

Yep.

---

### Post by kuio on 2008-06-07
> **ChameleonDave said:**
> Yep.

Thanks for the effort Dave but I just reinstalled Ubuntu. Works fine again. :)

---

### Post by risent on 2009-10-23
You just need to delete the "~/.local" directory!

---

