---
title: "Bash script for deletion of .mp3 files..."
date: 2007-06-24
forum: General Help
---

### Post by schnabea on 2007-06-24
Hey all I am still learning Linux and now I think I am ready to start learning to write my own scripts. Specifically I am looking for a script that will scan my music folder and its sub directories and delete any file with an .mp3 file extension... I am converting my entire collection to ogg vorbis and have no need of the mp3 files after they are converted...

Any good tutorials around to start learning this stuff?

---

### Post by Old *ix Geek on 2007-06-24
You really don't need a script for this.  Take a look at the **find** command (**man find**), paying particular attention to its **-delete** and/or **-exec** options.  This one command by itself can do exactly what you're describing. :)

---

