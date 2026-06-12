---
title: "[SOLVED] folder size  4096 - why"
date: 2007-10-09
forum: General Help
---

### Post by be4truth on 2007-10-09
Does somebody know why the folder size in the terminal is always  4096 ?

---

### Post by thirddeep on 2007-10-09
This is the default size of the file that holds all the pointers to the files inside the "folder".  Remember that in UNIX everything is a file.

If you put a LOT of files in that directory, this size will increase.

I hope my explanation is clear :-)

Thd.

---

### Post by hardyn on 2007-10-09
because a folder is just a file, a special file... and the data tha is contained within  that file is 4096b.  I would like to give you a better explination, but my OS text book is not handy.

---

