---
title: "rdiff remove-older-than: fatal error"
date: 2007-03-27
forum: General Help
---

### Post by martal on 2007-03-27
My rdiff-backup script is finally working OK, until I add the 'remove-older-than 2D'

From command, I get: Fatal Error: Wrong number of arguments given.

Here is the script:

#!/bin/bash
sudo /usr/bin/rdiff-backup --remove-older-than 2D --exclude-sockets --exclude-filelist /home/martin/Scripts/rdiff/exclude.txt / /media/LaCie/rdiff/test/

Appears to be good syntax. What's wrong?

---

### Post by martal on 2007-03-28
Fixed.

The error message did tell me to read the man page. :( 

Which I did, eventually.

rdiff-backup with a remove-older-than xy has to be run by itself, not as part of a backup.

Scripts now written. Everything working. For now.

---

