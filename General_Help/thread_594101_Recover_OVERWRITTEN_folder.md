---
title: "Recover OVERWRITTEN folder?"
date: 2007-10-27
forum: General Help
---

### Post by MrSootentai on 2007-10-27
I accidentaly moved a file with the same name as folder with my programming classes assignments.
So I ended up overwritting the work i was just about to turn in.
Before anyone says the whole backup thing...I do. I backup all the files everyday. It's just that I just finished this assignment today and hadn't backed up yet.

So anyone to recover an overwritten folder?

---

### Post by energiya on 2007-10-27
If you use ext3 there is a small chance (because its the best supported) but you might end up using more time than it would be necessary to remake the project (I'm not really sure, I only tried once a few months ago but didn't managed to restore my files)

My suggestion: make a small program/script that will backup ONLY your project files every, lets say, 10 min (maybe a cronjob) and to be sure you have a useful backup "backup the backup" so you end up with something like project -> 10 min backup -> 20 min backup -> 30 min backup -> 1h backup.  I hope you understand what I'm trying to say, and sorry if this isn't the answer you were waiting. I know how frustrating things like this are.

---

