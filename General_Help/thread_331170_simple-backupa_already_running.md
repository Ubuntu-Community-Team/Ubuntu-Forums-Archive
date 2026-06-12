---
title: "simple-backupa already running?"
date: 2007-01-04
forum: General Help
---

### Post by dannyboy79 on 2007-01-04
I installed simple backup a while ago and it was working flawlessly at first! Well now I have received a few different errors related to it. based on the config settings I chose for automatic incrementally backing up the folders and filers I chose it added an entry into cron daily I believe, this is what /etc/cron.d/sbackup looks like:
30 1 * * *      root    if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;
and like I said it was running smoothly. well the other day I received an error which I have already posted a thread for here [http://www.ubuntuforums.org/showthread.php?t=330501](http://www.ubuntuforums.org/showthread.php?t=330501) which is something about a segfault but now I received another email regarding sbackupd, this is the subject line: 
Cron <root@UBUNTU> if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;
and the body states this:
E: Another Simple Backup daemon already running: exiting
but when I do a ps aux | grep sbackupd or even sbackup nothing shows up??? Can anyone help?

---

### Post by dannyboy79 on 2007-01-16
bump, can't anyone else who runs sbackup help me with this?

---

