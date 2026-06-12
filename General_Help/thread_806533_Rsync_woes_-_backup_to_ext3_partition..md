---
title: "Rsync woes - backup to ext3 partition."
date: 2008-05-25
forum: General Help
---

### Post by musther on 2008-05-25
I'm having issues with rsync.  I'm using it to perform a backup of /home to a usb drive.  The USB drive is formatted as ext3, so there should be no permission or timestamp issues, but every time I run the backup, every file is copied rather than simply changed files.  I've been using the --size-only flag to make it simply check the file size, but why isn't it working with the default setup?

Cheers

---

