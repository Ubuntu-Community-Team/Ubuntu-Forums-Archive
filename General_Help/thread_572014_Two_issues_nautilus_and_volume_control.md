---
title: "Two issues: nautilus and volume control"
date: 2007-10-09
forum: General Help
---

### Post by Veinor on 2007-10-09
I've got two issues I need help with.
First: whenever I use the GNOME keyboard shortcuts to adjust my volume, all is well. Until I adjust it down to minimum, then wait for the on-screen volume display to disappear, then increase and decrease the volume again. It then goes to zero and mutes, and I can't use the keyboard shortcuts anymore. I have to do everything manually.

Second: I have no sidebar when I view nautilus; it just looks like the attachment. I tried building it from source a while ago, and that's when it all started, but I since have removed all the libraries in /usr/local, and run an apt-get purge and reinstall on nautilus and libeel, so that should have fixed it. F9 does nothing, and I have no sidebar-related options in my view menu.

---

### Post by JurB on 2007-10-10
Have you tried running gconf-editor?
I'm sure there is a sidebar option somewhere in apps > nautilus..

---

### Post by Veinor on 2007-10-10
Fixed it; I had to set /apps/nautilus/preferences/always_use_browser to true.

---

