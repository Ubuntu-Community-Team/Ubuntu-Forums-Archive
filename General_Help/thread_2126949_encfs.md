---
title: "encfs"
date: 2013-03-18
forum: General Help
---

### Post by merlinus on 2013-03-18
I have installed encfs and the gnome encfs manager.  I can select a folder to be encrypted, which is in a separate partition from /home, but seemingly cannot change the suggested mountpoint, which I do not want to be in /home/encfs/.  Is this possible?  Or do I have to create the mountpoint directory first?

Also, will files copied directly into the encrypted folder be automatically encrypted?  And am I correct in that I need to mount the encrypted folder, and then view and/or edit the files at the specified mountpoint?  

Their is very little documentation available for gnome encfs manager, and searching the forum did not help.

---

### Post by merlinus on 2013-03-18
Figured out how to do this.  Reinstalling the software helped.

---

### Post by markbl on 2013-03-18
FYI, I like and use encfs frequently but could not find a nice simple client. So I created my own which I have been using daily for many years now. See [https://github.com/bulletmark/encfsui](https://github.com/bulletmark/encfsui).

---

