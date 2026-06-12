---
title: "[SOLVED] Eye of Gnome can't open xpm images?"
date: 2007-10-23
forum: General Help
---

### Post by FuturePilot on 2007-10-23
I swear it used to be able to. If I try to open an xpm image it either looks like it's going to open it but then nothing ever opens or Eye of Gnome opens but with no image in it. Is this a bug?:confused:

Hmmmm

(eog:22524): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `EogWindow'

(eog:22524): EOG-CRITICAL **: eog_list_store_length: assertion `EOG_IS_LIST_STORE (store)' failed

(eog:22524): EOG-CRITICAL **: update_action_groups_state: assertion `EOG_IS_WINDOW (window)' failed
checking for valid crashreport now

---

### Post by FuturePilot on 2007-10-23
Ah, it's been fixed. Waiting for update.....

eog (2.20.1-0ubuntu1) gutsy-proposed; urgency=low

  * New upstream version:
    - Correctly set message area style
    - Bug fixes:
      - #482752, crash when opening a tiff image (eog_image_load)
      -   #475645, When an image is saved, the selection is lost (LP: #152785)
      -   #476313, plugins about dialog is not gtk+-2.11/2.12 ready
      -   #477550, fileformat combobox in save-as-many dialog is empty
      -   #479029, eog crashes when showing Image Collection
      -   #479400, Renamed files vanish from the collection 
      -   #479884, Mouse dragging UI broken.
      -   #482128, **Hangs on XPM file**
      -   #486057, "SetAsWallpaper" functionality doesn't launch background 
           properties (Felix Riemann)
    - New and updated translations: it, ko, be@latin, sl
  * debian/patches/90_from_svn_fix_duplicate_widget.patch:
    - dropped as got fixed upstream
  * debian/patches/91_from_svn_fix_mimetype_crasher.patch:
    - dropped as got fixed upstream
  * debian/patches/92_from_svn_update_images_collection.patch:
    - dropped as got fixed upstream

---

