---
title: "Evolution crashing and crashing and crashing."
date: 2007-10-23
forum: General Help
---

### Post by medeshago on 2007-10-23
I'm running gutsy. Evolution started to crash since i don't know when. If I try to open the Preferences, it crashes; if i try to save a file that has been sent, it crashes. Don't know what it is, don't know what to do.

Terminal Output:
Exepción de coma flotante (core dumped)

---

### Post by nolith on 2007-10-28
I've got the same problem.

Have you found a solution?

---

### Post by dcstar on 2007-10-28
> **medeshago said:**
> I'm running gutsy. Evolution started to crash since i don't know when. If I try to open the Preferences, it crashes; if i try to save a file that has been sent, it crashes. Don't know what it is, don't know what to do.

Terminal Output:
Exepción de coma flotante (core dumped)

Rename your hidden .evolution directory, then restart Evolution, it will now create a fresh .evolution structure.

If things work then there is a corrupt setting in your configuration somewhere, but you can now manually copy your existing e-mails (and other items) from the renamed directory into the new one.

---

### Post by nolith on 2007-10-28
It was a package problem, like for OpenOffice.
I've reinstalled all evolution* packages and has worked.

---

### Post by medeshago on 2007-10-28
I reinstalled evolution and i renamed the evolution hidden folder. Now, it won't even start:

```
medeshago@nosotros:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...

(evolution:8678): Gtk-WARNING **: Theme directory 16x16/actions of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 16x16/apps of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 16x16/categories of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 16x16/devices of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 16x16/emblems of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 16x16/emotes of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 16x16/mimetypes of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 16x16/places of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 16x16/status of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/actions of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/apps of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/categories of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/devices of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/emblems of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/emotes of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/mimetypes of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/places of theme gTangish-2.0 has no size field


(evolution:8678): Gtk-WARNING **: Theme directory 32x32/status of theme gTangish-2.0 has no size field

Loading Spamassasin as the default junk plugin
** (evolution:8678): DEBUG: mailto URL command: evolution %s
** (evolution:8678): DEBUG: mailto URL program: evolution
Exepción de coma flotante (core dumped)

```

If I disable the loading of the plugins (--disable-eplugin) it will open, but it won't let me open the preferences.

---

### Post by g8m on 2007-10-31
gtangish icon theme made my evolution go crazy too.

---

### Post by ocian on 2007-10-31
I'm also having the same problem and have that icon set. Anyone try default icons and seeing if it works?

---

### Post by ocian on 2007-10-31
okay, changed icon set to human and it works fine. Seems the gtangish icons screw it up

---

