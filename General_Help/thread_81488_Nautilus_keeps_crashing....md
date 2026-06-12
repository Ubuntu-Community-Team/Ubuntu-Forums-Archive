---
title: "Nautilus keeps crashing..."
date: 2005-10-24
forum: General Help
---

### Post by Beggar on 2005-10-24
I just did a fresh install of breezy, and so far havent had any problems, except one, whenever Im in nautilus it seems to crash on me (to the point where I gave up on using it because I cant get anywhere). Everytime it stops it reloads, then opens up an extra nautilus window. I was just wondering if anyone else is having a similar problem, or if its something that has already been fixed.

---

### Post by Kyral on 2005-10-24
Hmm, this is the first I have heard of this. You may want to file a bug.

---

### Post by huwshimi on 2005-11-11
I have the same thing happening. Seems to be .jpgs

Anyone know a solution?

Cheers.

---

### Post by ossi on 2005-11-11
Hi!

Try to do the following - go to a directory where there is no pictures in it. Go to preferences and switch off the creation of thumbnails. When it works then, it had something to do with the creation of the thumbnails. I had a similiar problem, but it looks like the Hardware was to blame, because next day my RAM broke down. I can't tell whether its the Hardware or Software, but just try and probably have a look at the hidden .thumbnails directory in your home directory. Probably there are too many files in it so Nautilus can't handle. Hope I could help. You can ead here what happened to me:

[http://ubuntuforums.org/showthread.php?t=84140&highlight=nautilus+major]("http://ubuntuforums.org/showthread.php?t=84140&highlight=nautilus+major")

---

### Post by kperkins on 2005-11-11
There's an update for nautilus today (applying some Debian patches for a bug that sounds similar to yours).  Try upgrading.

---

### Post by rbp on 2006-01-27
thanks for the info, I had the same problem but a .swf file was the culprit.

---

