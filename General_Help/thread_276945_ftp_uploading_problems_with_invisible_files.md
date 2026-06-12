---
title: "ftp uploading problems with invisible files"
date: 2006-10-13
forum: General Help
---

### Post by L2wis on 2006-10-13
Hey all, im having dire problems uploading my website via any ftp client due to these invisible files they keep trying to upload...

When i click to upload the entire website it gets hung up on files such as style.css~ and nav.php~ When i goto the folder these are being sent from there isn't anything there but the proper file i want to upload....

I'm guessing these are temp files or something, **how can i get rid of them and stop them from being created as they're giving me headaches!**

Regards

Lewis

---

### Post by PriceChild on 2006-10-13
Are there any open applications with edited and unsaved versions of these files open?

Close them and try again.

---

### Post by L2wis on 2006-10-13
none open or being used. I think they are there from earlier when i edited, and i've rebooted since they were edited... they seem to hang around :/

---

### Post by fragos on 2006-10-14
In Nautilus do a <Ctrl>H and you will be able to see these backup files.  They probably are backups from gedit.  Once visible in Nautilus they can be deleted in the normal way.  By default gedit keeps the last backup around, and deletes the older ones.

---

### Post by L2wis on 2006-10-14
hey m8, i've got it sorted now :) i went into gedit and turned off that feature. Many thanks :)

Regards

---

