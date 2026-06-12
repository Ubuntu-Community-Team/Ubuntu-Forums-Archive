---
title: "[SOLVED] Backup and Restore Ubuntu"
date: 2008-04-28
forum: General Help
---

### Post by bilijoe on 2008-04-28
I find this hard to believe, but after a reasonably thorough search, I can find no tutorial, how-to, or even a thread on how to back up and restore an entire [Ubuntu] system.  My 8.04 upgrade went seriously South, and I need to restore from the backup I made just before I started the upgrade.  (In a previous life, I was the administrator of a Unix system.  I can't believe how much I've forgotten, but, along with the man page, I was able--I hope--to manage to get a good copy (tar) of my entire system).  Now I need to restore it (over top of the bad 8.04 system?), and am concerned that what I've forgotten (which is most of what I knew) might land me in serious trouble, and leave me with no working system at all.  Also, at some point [soon], I am going to want to migrate my entire system to a larger hard drive.  Is this stuff just so simple and I so dense that I can't figure it out. but it's still not worth somebody writing a nice little (reassuring) how-to for?  Or was searching the forums for "backup and restore" not a good enough approach.  (Just for a laugh, you should try that search.  It brings up some very non-relevant articles--like "Why I love VISTA", and "IF you have VISTA, why are you still using Linux?"  What either of these has to do with backing up or restoring anything is beyond me, but the search brought them up, along with over a hundred other articles, none of which seemed to address the simple act of backing up and restoring a system.  Help!  Please!  I'd think one of you Linux gurus out there should be able to knock out a nice little (one page?) how-to in under 20 minutes--or point me to one that's already out there that I somehow missed.:popcorn::popcorn:

---

### Post by kingtaurus on 2008-04-28
I haven't used timevault myself (but I've heard its functionality is fairly impressive). It provides some better backup functionality than just tar-gzipping stuff (similar to a version system). You can also use rsync for backup. Also available is sshfs (which allows you to mount a remote filesystem or directories using fuse and ssh).

[http://howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10]("http://howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10")

---

### Post by Tews on 2008-04-28
I recommend that you try Quick-Start .. Developed for Ubuntu see pic

[IMG]http://www.libertymanor.org/menu.png[/IMG]

Go Here ==>> [http://quickstart.phpbb.net/index.php]("http://quickstart.phpbb.net/index.php")

---

### Post by dje on 2008-04-29
Take a look at linbaku at the blue link in my signature

dje

---

### Post by tliotis on 2008-04-29
thanks dje i use it right now!

---

### Post by dje on 2008-04-29
> **tliotis said:**
> thanks dje i use it right now!

No problem tliotis, if you have any problems please post in [this thread]("http://ubuntuforums.org/showthread.php?t=754816") or PM me

thanks,
dje

---

