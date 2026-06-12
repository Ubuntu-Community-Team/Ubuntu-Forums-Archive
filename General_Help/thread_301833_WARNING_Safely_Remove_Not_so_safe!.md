---
title: "WARNING: Safely Remove: Not so safe!"
date: 2006-11-17
forum: General Help
---

### Post by kverde on 2006-11-17
I just discovered that choosing to "Safely Remove" a USB drive in Kubuntu 6.10 is a little deceptive.  The drive disappears from the desktop almost immediately leaving one to assume that the drive is safe to remove.  Actually, data may still be being written to the drive for some time afterwards (if you had chosen to copy a large file).  Removing the drive at this point is not safe.  

The visual feedback from Kubuntu is that the drive is safe to remove because the command "Safely Remove" seems to imply that it is safe to remove once the icon disappears from the desktop.  This is not the case as I confirmed with an MP3 player that shows when data is being written to the disk. 

Any thoughts on this?  Should a bug report get filed?  Is there a way to make USB drives mount with the "sync" option?

---

### Post by slavik on 2006-11-17
in GNOME, the icon doesn't dissappear right away, it first shows a progress bar basically saying 'please wait' ... I think you should file it as a bug.

---

