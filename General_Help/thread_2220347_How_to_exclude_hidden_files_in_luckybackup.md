---
title: "How to exclude hidden files in luckybackup"
date: 2014-04-27
forum: General Help
---

### Post by dtree46 on 2014-04-27
Setting to exclude Trash folder in luckybackup works.
However, how is '/.local/share/Trash' excluded, and/or other hidden files?

Thanks,
dlw

---

### Post by ajgreeny on 2014-04-27
I don't know luckybackup apart from the fact that it is a GUI frontend for rsync in which you exclude files with the option **--exclude /path/to/file**

It is probably safest to use the full pathway so for your user trash it would be **--exclude /home/username/.local/share/Trash/***

Presumably luckbackup has some way of configuring what you can include or exclude in the backup, but I will have to let you try or search further as I use rsync or grsync for my backups.

---

