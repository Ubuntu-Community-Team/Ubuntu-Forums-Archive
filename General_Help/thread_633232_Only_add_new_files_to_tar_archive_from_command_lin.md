---
title: "Only add new files to tar archive from command line"
date: 2007-12-06
forum: General Help
---

### Post by dje on 2007-12-06
I use the followng command to backup my computer
 ```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/media /
```

How can i change it so it only adds files and folders to the archive if they have changed since i last backed up (the new backup always has the same name and overwrites the old one). I think you can do this?

---

### Post by dagnabit dang doohickey on 2007-12-06
I can't help but thing there's probably a more elegant way of doing this, but here's an idea:
```
bunzip2 backup.tar.bz2 ; tar upvf backup.tar *[all-your-excludes]* / ; bzip2 backup.tar
```

Note: you may want to change your previous exclusion of backup.tar.bz2 to backup.tar*

---

