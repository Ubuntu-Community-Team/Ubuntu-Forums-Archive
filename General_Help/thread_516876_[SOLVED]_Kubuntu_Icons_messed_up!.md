---
title: "[SOLVED] Kubuntu Icons messed up!"
date: 2007-08-03
forum: General Help
---

### Post by fireworld2406 on 2007-08-03
My icons are missing in Kubuntu 7.04. I loaded the KDE Control Center and I changed the theme under Theme Manager. Once I somewhat figured out how to get back to the regular look (it's still kind of messed up), alot of icons are missing. For example, in Konqueror, it doesn't show any buttons at all. Also, when I right click on the desktop, it shows the text, but not the little icons next to it. How can I restore my Kubuntu interface to its normal look and get the icons back. All help is appreciated.

---

### Post by strabes on 2007-08-03
If you make backups, just copy your backed up .kde folder back into your home directory. In kubuntu there's unfortunately no "default" theme so once you change it you can't get it back as far as I know.

---

### Post by fireworld2406 on 2007-08-03
I don't make backups, but I have got it partially back to normal (I have no idea how). Currently, the arrow icons in Konqueror are there, but they are black/gray instead of the colorful blue that they used to be. I wish I could get that fixed, maybe someone knows how.

---

### Post by strabes on 2007-08-11
In kcontrol, go to Appearance & Themes, Icons. Select Crystal SVG, apply and restart the X server with ctrl+alt+backspace (this might not be necessary.)

---

### Post by jd_k on 2007-08-23
I have the same problem, but changing the icon theme as suggested does not solve it (with or without restarting X). Any other suggestions?

---

### Post by jd_k on 2007-08-23
I ended up just deleting (or rather, renaming) my ~/.kde and ~/.kde-3.x folders and starting over.

It worked, but hat's not exactly a solution if it messes up the icons on any regular basis. I must be missing something obvious. :-/

---

