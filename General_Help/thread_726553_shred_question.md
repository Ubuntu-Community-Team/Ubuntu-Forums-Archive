---
title: "shred question"
date: 2008-03-16
forum: General Help
---

### Post by 3pinner on 2008-03-16
Running Ubuntu 7.10, ext3 file system.

I used shred to destroy a bunch of files I didn't need anymore.
when I used Tracker to search for a file with the same extension (mpg files to be specific), Tracker shows I still have a large number of these files, but there's nothing listed in Tracker to show where they are. For example, Tracker will say I have 100 mpg files, but only list the 10 or so that I have in a folder.

Why would Tracker still list the shredded files as existing?
How can I either reset Tracker so it only shows the files that DO exist, or make sure those shredded  files are gone?

thanks

---

### Post by sumguy231 on 2008-03-16
Tracker indexes your files for fast searching, so you need to force it to reindex whatever location they were in for it to realize they don't exist anymore. Same thing with locate on the command line. Use updatedb to update locate's database.

---

### Post by 3pinner on 2008-03-17
Thank you sumguy,
using terminal, how would I use the updatedb command to re-index what Tracker sees?
I've read the man on updatedb  but would appreciate some help before I attempt it.

Thanks!

---

### Post by sumguy231 on 2008-03-17
Just run
```
sudo updatedb
```
And enter your password. Wait a while, and it will finish eventually even though it doesn't display anything.

That's for locate, and has nothing to do with Tracker. To reload Tracker, you will have to do it from the Tracker settings I guess. I've never really used Tracker before. Check again though, because by now it may have updated the index itself anyway. Locate updates its database daily.

---

