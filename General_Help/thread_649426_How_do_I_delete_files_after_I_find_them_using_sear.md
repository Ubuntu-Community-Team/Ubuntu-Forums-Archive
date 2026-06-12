---
title: "How do I delete files after I find them using search function?"
date: 2007-12-24
forum: General Help
---

### Post by tmcarson1 on 2007-12-24
In windows (I know this isn't windows but looking for a way to do this), I was able to search for say *.mp3 and it would locate any file with mp3 extension, then I could select them all and delete them from the search window.

I tried this in ubuntu, it found all the files, but when I right click them the 'move to trash' function is greyed out.

The problem is I moved all my music files from my windows drive to my ubuntu drive, including the mp4 ones which my portable player does not support.

Now I would like to go and erase all those mp4 files so that all that is left is my mp3s.

Any ideas how to do this without having to go into every folder for every album and delete the mp4s?

Thanks!

---

### Post by taurus on 2007-12-24
You cannot move or delete anything outside your own $HOME directory.  To do that, you need to use sudo/gksudo.

<Alt>F2 -> gksudo nautilus

---

