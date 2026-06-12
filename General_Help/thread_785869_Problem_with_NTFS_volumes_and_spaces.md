---
title: "Problem with NTFS volumes and spaces"
date: 2008-05-07
forum: General Help
---

### Post by DizzyTech on 2008-05-07
When I originally installed Hardy on my laptop, I used Wubi from the CD.  Everything worked fine, but there were certain problems with my Vista NTFS partition.  My usual practice with Ubuntu is to permanently mount my Vista partition and create a symbolic link between my home folder's folders and those in Vista.  In other words, I link C:\Users\[username]\Music to /home/[username]/Music.

In Wubi, it worked all right.  My biggest problem was that Rhythmbox couldn't import automatically anything with spaces in them.  I'd set its library directory to /home/[username]/Music and tell it to automatically import, but the only songs that would import are songs with no spaces in their path (e.g., /home/[username]/Weezer/Maladroit/December.mp3) and all the rest (e.g., /home/[username]/R.E.M/Accelerate/Supernatural Superserious.mp3).

As a result of this, I decided to install Hardy from the CD.  Everything worked fine for some time (including NTFS) until I broke my wireless (don't ask, it's fixed now), so I reinstalled Hardy from a freshly downloaded image and isntalled it.  So... guess what?  Same problem.  I've mounted Vista once by going to Places >> Vista.  The problem also occurs if I (unmounting Vista first) set up the NTFS partition permanently using ntfs-config.

Although a simple workaround would be to rename all of my files, or manually import songs, not only is it a pain to track what I put in my library but also that Windows (because WMP and iTunes love to fight over my folder structure) pisses itself everytime something changes.

Any ideas?

---

### Post by DizzyTech on 2008-05-09
Bump... ?

---

### Post by joshsmith on 2008-05-10
hey,
you are experiencing a temporary bug, with rhythmbox which is currently being worked on and should be fixed soon.

however, all you need to do is go into rhythmbox > edit > preferences > music
and reselect the location of your music, ie click browse and browse to the same folder and click ok
check the watch box, and your library will fill up in a couple of seconds.


ps, might be a good idea to remove all the files from your library at some point, and then rhythmbox will automatically find them again (will stop you getting duplicates)

---

