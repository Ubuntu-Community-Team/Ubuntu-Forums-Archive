---
title: "Is there an app that does this?"
date: 2008-02-25
forum: General Help
---

### Post by unbuntu on 2008-02-25
I'm looking for an application (preferrably in Gnome) that can show the content of an arbitrary folder on virtual desktops.

For example, by default, the Ubuntu desktop shows items in the folder ~/Desktop and every other virtual desktops uses this folder too.  Would I be able to configure it so that, say, desktop 2 shows ~/Music and desktop 3 shows ~/Video and so on?

TIA.

---

### Post by jeffus_il on 2008-02-25
Yes , if each desktop had a different user running it, since the desktop folder is defined in the gconf data which is per user.

I think I may be wrong about the Desktop folder being defined in gconf.
In gconf it can be changed to the home folder,  and the "Desktop" folder may be hard coded in nautilus.

The is an Option of linking the Desktop folder to other folders.

---

### Post by unbuntu on 2008-02-25
> **jeffus_il said:**
> The is an Option of linking the Desktop folder to other folders.

Then each desktop (I'm gonna use  "workspace" for this to be consistent with gnome's term) would still be showing the same content since they're still pointing to the same folder, right?

---

### Post by Acglaphotis on 2008-02-25
I asked this same question a long time ago :). Sadly, it appears that there is no solution for this problem.

---

