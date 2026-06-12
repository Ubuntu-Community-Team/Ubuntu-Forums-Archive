---
title: "Making auto backups"
date: 2007-02-17
forum: General Help
---

### Post by mr.propre on 2007-02-17
I've been looking for a wile now, but didn't found the best way to automatically backup certain folders to a network or a ftp account.

Basically, what I want is to backup some file, once a week to a network or my ftp account if available, else it needs to stay in sort of Queue until it' available.
The files must be compressed if possible.

Can somebody give me a good easy program to backup? I prefer a GUI.

Thank you

---

### Post by halfvolle melk on 2007-02-17
No GUI solution but still a really good one is rsync + cron. Do a forum search on **rsync cron** and you'll find instructions like these (post #2):
[http://ubuntuforums.org/showthread.php?t=363151](http://ubuntuforums.org/showthread.php?t=363151)

---

### Post by jure1873 on 2007-02-17
The most customizable is a bash script you create with rsync and cron, but there are also gui programs that can help you. Just google around a little for cron gui or rsync gui.

[http://www.debianhelp.co.uk/rsyncweb.htm](http://www.debianhelp.co.uk/rsyncweb.htm)
[http://kde-apps.org/content/show.php?content=33545](http://kde-apps.org/content/show.php?content=33545)
[http://www.setara.org/screenshots.html](http://www.setara.org/screenshots.html)

---

### Post by mr.propre on 2007-02-18
Thank you for the information, I will have a look at it and post you if I have any problems.

---

