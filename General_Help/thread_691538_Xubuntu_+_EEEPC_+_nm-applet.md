---
title: "Xubuntu + EEEPC + nm-applet"
date: 2008-02-08
forum: General Help
---

### Post by yeleek on 2008-02-08
Hi,

Replaced std eeepc os with xubuntu today.  Seems great.  However the nm-applet is loading twice in the system tray.   I can kill one of them manually via system monitor, but i'd like to stop the 2nd instance loading altogether.  Any ideas?

Thanks

---

### Post by pebo on 2008-02-08
From [this]("http://www.nabble.com/Multiple-Instances-of-nm-applet-to11699737.html") post on another forum: > There was advice on Ubuntu Forums:
> open the file ~/.cache/.sessions/xfce4-session-????? and remove all
> entries of nm-applet but one. Renumber the Client? headings
> appropriately and set Count equal to the last client number + 1. Save.
> Logout w/out saving the session and you are done. It's a pita but it worked for me!

---

### Post by yeleek on 2008-02-09
> **pebo said:**
> From [this]("http://www.nabble.com/Multiple-Instances-of-nm-applet-to11699737.html") post on another forum: It's a pita but it worked for me!

Thats great - many thanks working fine now.

---

