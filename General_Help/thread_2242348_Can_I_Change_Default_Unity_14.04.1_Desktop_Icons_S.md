---
title: "Can I Change Default Unity 14.04.1 Desktop Icons Size?"
date: 2014-09-01
forum: General Help
---

### Post by 2CV67 on 2014-09-01
The default size of any icons I place on the desktop seems grotesquely large.

I know I can right-click & resize individual icons, but is there a way to reset the default size?

Note: I am not talking about icons in the Launcher - resizing those was obvious.

Thanks!

---

### Post by mc4man on 2014-09-01
The icon size is set by a gsetting > org.gnome.nautilus.icon-view default-zoom-level
Note that it will affect all not just the Desktop

Can  be set in nautilus > preferences > Views or in  dconf-editor or thru gsettings, there are 7 values available

---

### Post by CantankRus on 2014-09-01
As nautilus draws the desktop, the size is whatever you have set in icon view defaults of the file browser.

---

### Post by 2CV67 on 2014-09-01
> **CantankRus said:**
> As nautilus draws the desktop, the size is whatever you have set in icon view defaults of the file browser.

Ah! Thanks!

I always use list view in Nautilus, so had never touched the icon-view size, which was set at 100%.

Now everything is fine!

Thanks again! (both replies) :D

---

### Post by lukon on 2015-02-01
None of these things work for me.

I run 14.04.1 Unity.

There seems to be no way to change nautilus settings.

Edit ------------------------------

Ok. I just found the solution.

Open a random window to view some random files. This is a nautilus window.

The window's title bar will display the name of the random folder you are viewing.

Mouse your cursor over that title bar and it switches to become a menu bar.

From that menu bar, select Edit>Preferences

Up pops a "Files Preferences" window where you can adjust icon sizes and other things.

Done!

---

