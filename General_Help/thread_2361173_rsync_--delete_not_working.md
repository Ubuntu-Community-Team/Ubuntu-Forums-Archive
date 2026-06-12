---
title: "rsync --delete not working"
date: 2017-05-13
forum: General Help
---

### Post by jaarvidsen on 2017-05-13
hi
after lots of searching and trying and failing ive given up and must resort to asking the community. can someone tell me why this command doesent delete files/dirs from the destination dir?

rsync -auq --progress --delete --exclude=.thumbnails/ --exclude=.cache/ --exclude=Desktop/ --exclude=.adobe/ /home/USERNAME/ /media/USERNAME/2tb/desktop1/home1

i basically just want to keep a backup of my homedir and if ive deleted a file or dir from my homedir i want the command to also delete those files/dirs from the destination but its just not working, result is that my backup is full of files that are many years old. i swear it worked maybe 10 years ago when i made the script but maybe 5 years ago it stopped deleting..

---

### Post by dragonfly41 on 2017-05-13
Perhaps try running the command in gui grsync .. dry run mode .. to debug your command

---

### Post by Impavidus on 2017-05-13
Besides, we usually recommend versioned backups. Suppose some file gets corrupted, deleted or modified, then you make a new backup and then you notice that you need the old version of the file again. That happens far more often than a broken hard drive, which is the only thing your backup routine protects against. Trust me, I learned it the hard way.

---

### Post by jaarvidsen on 2017-05-13
> **Impavidus said:**
> Besides, we usually recommend versioned backups. Suppose some file gets corrupted, deleted or modified, then you make a new backup and then you notice that you need the old version of the file again. That happens far more often than a broken hard drive, which is the only thing your backup routine protects against. Trust me, I learned it the hard way.

ive got a separate backup for that that does NOT delete anything on purpose. i DO want delete for this command, thus this is what i requested


@dragonfly41 i had no idea that grsync even existed, will play around with it when i have the time a little later

---

### Post by HermanAB on 2017-05-13
If you use --delete and --exclude together, what is in the excluded location won't get deleted.

Any errors will also prevent deletions.

I also prefer to add max-delete to prevent a catastrophe due to some error.

You can try:
--delete --ignore-errors --max-delete=20 --delete-excluded

---

### Post by jaarvidsen on 2017-05-13
@HermanAB
--ignore-errors did the trick, now it works as i expected
thanks a lot :))

---

