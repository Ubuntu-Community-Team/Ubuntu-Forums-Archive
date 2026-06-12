---
title: "Users can't mount volumes on networked machine"
date: 2004-11-16
forum: General Help
---

### Post by fjleal on 2004-11-16
I have a Ununtu box as a network client using NIS, and I realized that users from the NIS domain can't mount/unmount volumes. They can't even format a floppy, for a dialog complaining about lack of permission is shown when they run the formatter program from the Gnome menu. They can't mount the CD also.

I worked out this problem "chmoding" the devices (under /dev) to 777. Is it the preferred method? Why can't users acces the volumes? Can somebofy please explain to me the system politics involved? Thank you very much.

---

