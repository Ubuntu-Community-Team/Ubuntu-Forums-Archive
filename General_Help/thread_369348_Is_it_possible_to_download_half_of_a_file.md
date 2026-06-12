---
title: "Is it possible to download half of a file?"
date: 2007-02-24
forum: General Help
---

### Post by Roasted on 2007-02-24
I have 2 drives and an rsync script set up. 2nd drive is strictly for backup purposes... no OS is on it.

Question... Say I have a large torrent running, and I pause the download during the day, and then run my rsync script. Is it possible that only half of the file(s) in the torrent that I downloaded would of been "registered" by the operating system? If so, when I rsync, what happens? Does that portion of the file get transferred? 

If so, then what if I run rsync again? Will it see the file name and be like, oh, I already did this one, and skip it? Therefore leaving me with essentially HALF of a file?

---

### Post by linux_kid on 2007-02-24
I'm not completely understanding your issue, please be more specific with your problem.

---

### Post by SeanTater on 2007-02-24
If you gave the --ignore-existing option, you'll end up with a half of a file on your backups. If you did not specifically tell it to, by using that option, don't fret. Your file will be transferred entirely to the backups provided that it exists in entirety in the original..

In your case:

* You start the torrent

* You stop it half-way

* You sync it and there is a half of a file in both places

Now, provided you continue, this happens:

* You continue the downloading

* The torrent completes downloading

* You sync again, and the *whole* file is in both places.

---

### Post by Roasted on 2007-02-25
Thanks bud. The only tags I used I believe were -a --progress --delete, or something?

---

