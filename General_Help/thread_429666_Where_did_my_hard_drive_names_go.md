---
title: "Where did my hard drive names go"
date: 2007-05-01
forum: General Help
---

### Post by muguwmp67 on 2007-05-01
In Edgy, my hard drives imported their names from windows (they were named in nautilus, Windows, Media, etc).  Mine used to be nice english labels.  Now they are named from their device names (hda1, sdb2, etc)

I liked it much better the other way, how do I get the names back in nautilus?

---

### Post by jakev383 on 2007-05-01
In /media you will see the hdax names. You'll need to create directories here with the names you want, and then edit your /etc/fstab file. Instead of having the drive mount to /media/hda1 have it mount to /media/Windows or whatever you call the directory.

---

### Post by muguwmp67 on 2007-05-01
Do I create symbolic links to the existing directories, or simply new directories?

---

### Post by jakev383 on 2007-05-02
New dirs if you're going to change the handles in fstab

---

