---
title: "copy &amp; paste but skip duplicates"
date: 2015-03-12
forum: General Help
---

### Post by palmgrower on 2015-03-12
I have 2 folders. SMALL FOLDER (which is mp3 player) has 400 mp3 files. LARGE FOLDER has these 400 plus 200 mp3 files. I would like to copy and paste the extra 200 files to SMALL FOLDER. Is there a routine that compares the two folders and copy/paste extra files only?
Thanks.

---

### Post by Ko_Char on 2015-03-12
I use FreeFileSync. [http://www.freefilesync.org/](http://www.freefilesync.org/)
Better than others in my opinion.

---

### Post by ajgreeny on 2015-03-12
You already have rsync in a default installation and grsync which is a GUI for rsync is available in the repos and that will also do exactly what you want.  It will also incrementally update files if they have changed since the previous time it was run.

I can not comment about freefilesync as I had never heard about it and rsync already works extremely well for me; I use it for my backups, so I have no reason to investigate further.  I also prefer to use applications from the official repos if possible.

---

### Post by Dennis N on 2015-03-12
> **palmgrower said:**
> I have 2 folders. SMALL FOLDER (which is mp3 player) has 400 mp3 files. LARGE FOLDER has these 400 plus 200 mp3 files. I would like to copy and paste the extra 200 files to SMALL FOLDER. Is there a routine that compares the two folders and copy/paste extra files only?
Thanks.

From the source folder, you can use **cp -n** to copy only files whose names don't already exist in the destination folder. In other words, this will not overwrite any existing files.

cd to source folder and use:

```
cp -n *.mp3 <destination-folder> 
```

---

### Post by Bucky Ball on 2015-03-12
I use Luckybackup. It's in the repositories (Software Centre/Synaptics). Just install from there.

---

