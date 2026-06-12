---
title: "Want to restore just one file with Ubuntu 12.04 backup program"
date: 2013-01-10
forum: General Help
---

### Post by 777funk on 2013-01-10
I don't want to restore everything back to a certain date, just one file, how do I do this?
thanks,

---

### Post by timgood on 2013-01-10
Browse to the folder containing the file you lost.
    Click File &#9656; Restore Missing Files&#8230;
    When the Restore dialog appears, it will scan for files that are in the backup but no longer in the folder.
    When you see the file you want to restore appear, select it and click Forward.
    Review your selections and click Restore.

In the worst case scenario you can use the command line. [This]("https://live.gnome.org/DejaDup/Help/Restore/WorstCase") resource is excellent and has saved my bacon a few times.

Hope this helps.

---

### Post by 777funk on 2013-01-10
Thank you Tim! I will try this.

---

### Post by 777funk on 2013-01-10
Ok just tried this and I don't see any menu (File header) in the Folder navigation and I don't see anything but a full restore in the Backup program (icon looks like a Safe in Ubuntu 12.04). 

Having a hard time finding this.

---

### Post by timgood on 2013-01-11
> **777funk said:**
> Ok just tried this and I don't see any menu (File header) in the Folder navigation and I don't see anything but a full restore in the Backup program (icon looks like a Safe in Ubuntu 12.04). 

Having a hard time finding this.

The command should be in normal nautilus view of the folder with the missing file. A click  on File (menu item on top panel) should bring up the option. This is not in the folder view of your backup, but in the ordinary view of folders in your home directory.

---

