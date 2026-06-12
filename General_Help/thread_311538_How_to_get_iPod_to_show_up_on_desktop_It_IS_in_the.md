---
title: "How to get iPod to show up on desktop? It IS in the places menu."
date: 2006-12-03
forum: General Help
---

### Post by strabes on 2006-12-03
My iPod is automounting and showing up in the places menu and in nautilus. It just doesn't show up on my desktop like it used to. Other mountable volumes like my shared ext3 data partition appear on the desktop, and volumes_visible is checked in gconf-editor/apps/nautilus/desktop. Is there something that is preventing my ipod from appearing on the desktop?

---

### Post by aysiu on 2006-12-03
I don't know if there's something preventing it from appearing on the desktop, but the "volumes" that are "visible" are usually mounted within the /media directory.

Do you know what the mount point is for your iPod?

If not, can you post the output of this command? ```
df -h
```

---

### Post by strabes on 2006-12-03
Yeah it's mounted on /media/ipod - the default mount location for ipods. aysiu - I used the script you wrote on your website to change thunar to the default file manager and then I used the other script to change it back to nautilus. Maybe that messed something up with nautilus handling the desktop or something? I have no idea so I'm just throwing ideas out there. I'm using beryl/xgl; that also might have something to do with it although it still doesn't appear on the desktop in my normal gnome session either.

By the way - nice to see there are other Christians on these boards. Even though you're pro-choice :)

---

### Post by aysiu on 2006-12-03
I doubt the script has anything to do with it, but you can double-check. If you go (using *gksudo nautilus*) to /usr/share/applications and check out the commands associated with Home Folder, File Browser, File Management, Computer, and Open Folder. Right-click the icon, go to **Properties** and **Launcher** to see the command.

Beryl may also have something to do with it, but I don't use Beryl, so I'm not sure.

And, believe it or not, [there are actually a lot of Christians on the boards... almost as many as there are Atheists.](http://ubuntuforums.org/showthread.php?t=297083) You might find some pro-lifers among them.

---

### Post by strabes on 2006-12-03
They're all set to nautilus in some form or another. Thanks for your help and contributions to the linux community.

Also thanks for that link to your religion forum post. That is nice to know. :)

---

### Post by strabes on 2006-12-11
bump

---

