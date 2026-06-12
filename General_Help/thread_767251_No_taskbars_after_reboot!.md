---
title: "No taskbars after reboot!"
date: 2008-04-25
forum: General Help
---

### Post by LieToPurify3 on 2008-04-25
I was installing updates and my computer froze, so I had to reboot and when I logged back in, my taskbars were gone! The system update window comes up every time I log back in.  Since it still comes up,I upgraded to 8.04 hoping that would reset the problem, but it hasnt.  Help!

---

### Post by Naatan on 2008-04-25
What I usually do in cases like this is that I open tty1 (at the login screen - don't login but press ctrl+alt+F1) and login, copy all of the contents of your home directory to a backup location and then clear out your home dir, login and you'll have a default ubuntu profile (default settings etc).

Now you can copy back the files you need (and only the files you need) from the backup location.

eg.

$ mkdir /tmp/backup
$ cp -Rfv /home/myuser/* /tmp/backup
$ rm -Rfv /home/myuser/*

If you have no idea what any of the above commands are for don't attempt this

---

### Post by LieToPurify3 on 2008-04-27
I just did what you said, but when I log back in, all I get is my desktop icons, and my update manager is up yet again!  Taskbars are still gone.  Any other ideas?  I just did a fresh install of 7.10 a few weeks ago and hardly use this laptop since its so old.

---

### Post by LieToPurify3 on 2008-04-27
help!

---

