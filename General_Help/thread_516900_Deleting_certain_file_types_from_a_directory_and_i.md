---
title: "Deleting certain file types from a directory and its subdirectory's"
date: 2007-08-03
forum: General Help
---

### Post by Jamesbowden on 2007-08-03
In my music directory I have around 3000 tracks, about half of which are .m4a, I wish to delete all .m4a files leaving only the .mp3 files (so that I can re-rip the .m4as to .mp3)

the files are organized like this:
~/Music/<Artist>/<Album>/<track>.m4a

and some like this

~/Music/<Artist>/<track>.m4a

what is is easiest and quickest way to delete all the .m4a files without removing any of my .mp3s

thanks.
James

---

### Post by yabbadabbadont on 2007-08-03
```
find ~/Music -type f -name "*.m4a" -exec rm -f {} \;
```
That should do it.

Edit: run that in a terminal window.

---

### Post by Jamesbowden on 2007-08-03
> **yabbadabbadont said:**
> ```
find ~/Music -type f -name "*.m4a" -exec rm -f {} \;
```
That should do it.

Edit: run that in a terminal window.

yay unix shell magic! I will try that I have finished re-ripping all my music.

 thank you very much

---

