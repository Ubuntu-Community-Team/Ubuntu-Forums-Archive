---
title: "Automounting windows partitions in kubuntu 6.10?"
date: 2006-11-13
forum: General Help
---

### Post by flummoxed on 2006-11-13
I just installed Kubuntu 6.10. I'm usually a gnome guy, but I decided to see what KDE was all about. One problem I'm having so far is it's not automatically mounting my windows hard drive, where I have all my music and stuff. Ubuntu 6.06 did this automatically. Kubuntu recognizes the hard drive, however, as I can see it in the Disk & Filesystems Administration panel. If I add an entry to fstab, will that make it mount my windows partition automatically every time I boot?

---

### Post by dannyboy79 on 2006-11-13
is this a removable drive or an internal drive? if it's internal than yes you have to add an entry in fstab for it to mount automagically. tjhe only way gnome would have done this automagically for ya is if the drive was present when you did the install and you made a mount point for it upon installation. it should have worked the same way in kde as I thought the only difference is the window manager. if it's a usb drive and it's plugged in then yes it should mount automagically, this is handled by hal, and pmount I believe, there has been a problem found with fat32 drives and automounting them with write access, apparently konkueror (bad spelling and I don't care) was making the drive only readable, it was due to the fat32 filesystem being flawed and the person had to run some kind of doschk  or something, here is th post if that's the issue other than just automounting. [http://www.ubuntuforums.org/showthread.php?t=289366&page=6&highlight=writing+to+external+drive](http://www.ubuntuforums.org/showthread.php?t=289366&page=6&highlight=writing+to+external+drive)

---

### Post by flummoxed on 2006-11-13
I just read the wiki article on mounting Windows partitions. Yes, it's an internal drive running windows xp. I just made the right entries in fstab and mounted it. Thanks for the quick reply.

---

### Post by dannyboy79 on 2006-11-13
np (no problem)

---

