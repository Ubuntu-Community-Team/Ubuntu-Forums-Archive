---
title: "problem with mpd and (nc)mpc"
date: 2007-03-01
forum: General Help
---

### Post by jfinkels on 2007-03-01
Ubuntu 6.10

According to <mpd --version>, mpd supports mp3 files, and i can play certain mp3 files with mpc. mpd will recognize and play files that are in the toplevel [music] directory. However, any mp3 files that are within a folder/subfolder under the toplevel [music] directory (i.e. "[music]>[artist]>[album]>[trackname].mp3") DO NOT show up in the database and CANNOT be played. Any ideas? All my FLAC files work just fine, including those in subfolders.

---

### Post by yabbadabbadont on 2007-03-01
Check the permissions of the subfolders to be sure that mpd can read them.  You didn't say, but I assume that you re-ran mpd with the "--create-db" option if you added the mp3 files in the subfolders after you initially created the mpd music database.

---

### Post by jfinkels on 2007-03-01
Aha! My mp3 files are all mode 700...there's the problem. Just need to change them all to 755. Thank you so much!

---

### Post by yabbadabbadont on 2007-03-01
> **jfinkels said:**
> Aha! My mp3 files are all mode 700...there's the problem. Just need to change them all to 755. Thank you so much!

You are welcome, but it should be 644, not 755.  There isn't any reason for mp3 files to be executable...  ;)

---

