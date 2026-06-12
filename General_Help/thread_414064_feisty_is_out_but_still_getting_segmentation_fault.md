---
title: "feisty is out but still getting segmentation fault in gnome-system-log"
date: 2007-04-19
forum: General Help
---

### Post by harty83 on 2007-04-19
Okay so I was hoping this would be fixed before feisty was released.  I'm still getting a segmentation fault when trying to run gnome-system-log.

```

alan@laptop:~$ gnome-system-log
Segmentation fault (core dumped)

```

Any ideas?

Alan

---

### Post by ronin2040 on 2007-05-17
i have a solution for you.

try moving everything in /var/log/ to a different location.

It may be best to check with a linux guru to make sure this wont break anything, but I'm assuming that the logs are only there for troubleshooting, and can safely be deleted.  Im keeping backups, however.

Im going to do a little tinkering and try to pin down which log was causing it.

EDIT:  the user.log had a series of ^@^@^@^@^@ on one line, and upon deleting those symbols, (sudo nano /var/log/user.log) the systemlog allowed me to read the file.  It may be a different file for you, i simply narrowed it by moving all logs to a tmplog folder, then moving them back one letter at a time (sudo mv tmplog/w* /var/log/) and opening the logs in gnome-system-log until it crashed.

Hope that helps :D

---

