---
title: "Backup Solutions?"
date: 2006-11-12
forum: General Help
---

### Post by Buelldozer on 2006-11-12
Hi,

I have about 40 Gigabytes of data that I would like to backup to DVD. What Ubuntu / *nix package can I use that will not only span this across DVDs but allow each DVD, and the files on it, to be individually readable when it's done?

Anyone?

---

### Post by syadnom on 2006-11-12
tar will do this job for you.  tar archives can all for individual file access via 'arc' or winrar in windows easily.

---

### Post by Buelldozer on 2006-11-12
I wasn't aware that tar could write to a DVD?!

---

### Post by tminuszero on 2006-11-12
tar won't write to a DVD by itself. I think what he was saying is that you can create a tar file, and split it into big chunks and then burn the chunks using your favorite DVD burning program. Something like:

tar -cvvzpSf - your_folder | split -b 4000m

You could also just use [KDar]("http://kdar.sourceforge.net/"). To install: 

sudo apt-get install kdar dar libdar3c2a

That has a nice GUI.

---

### Post by chalex on 2006-11-12
You could also look at sbackup: [http://sbackup.sourceforge.net/HomePage](http://sbackup.sourceforge.net/HomePage)

Why do you want to write to DVDs?  Dealing with a 10-disk backup set is a hassle.  What happens if one disk gets scratched?  If you use tar, the entire archive will be unreadable, AFAIK.

You may want to invest into an external HD or something like rsync.net.

---

### Post by gg234 on 2007-01-13
if you want to use dar try [this]("http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html") and for sbackup try [this]("http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")

---

