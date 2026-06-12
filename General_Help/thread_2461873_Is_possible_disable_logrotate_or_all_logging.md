---
title: "Is possible disable logrotate or all logging ?"
date: 2021-05-09
forum: General Help
---

### Post by aug7744 on 2021-05-09
I not need logs and need avoid useless writes on disk.
Is possible disable all system logs or logrotate ?
Using Stacer is displayed always when system is totally started was writed 20 MB on disk and in few horus more of 200 MB in partition disk / being that not was done softwares installation or configurations and less yet internet access.
An solution for that is repeated writes on disk is using an writenback with defer flush in ram , but I not see any utility that does it.

Thanks for your reply.

---

### Post by HermanAB on 2021-05-09
You can read all about it here [https://www.loggly.com/ultimate-guide/linux-logging-with-systemd/](https://www.loggly.com/ultimate-guide/linux-logging-with-systemd/)

---

### Post by Holger_Gehrke on 2021-05-09
Did you say '200 MB in one session' ? For comparison: the logs for the last **half year** on my machine take a bit more than **500MB**. If your system produces that amount of log data in a few hours there's something desperately asking for your attention. Read the logs to find out what's wrong. Might be some failing hardware. Might be a program set to log debug output. Fixing the problem will stop the log from growing at that terrifying speed.

Holger

---

### Post by TheFu on 2021-05-09
You could change the settings for logrotate and mount a ramdisk to /var/log/ to prevent hitting disk, but you'll want to be able to re-enable this (or have a toggle) to aid with troubles.  Plus, you'll probably want something like logwatch running daily so you don't miss critical stuff that gets put into the logs.

Had a client call for help.  They were having trouble restoring backups.  When I got there, found the backup tool had been corrupted and hadn't actually made a backup in over a year.  They lost a number of clients because they didn't have backups for the client data.  If they didn't have logs, I would have wasted way too much time and the client's money trying to recover nothing.

---

### Post by HermanAB on 2021-05-10
Note that logrotate isn't the problem - it doesn' create the logs, it just manages and compresses them.  So if anything, logrotate can save the day by reducing the log size.  The problem is whatever is broken and creating all the log entries.  So you need to read the logs and see what is written.  That is the whole purpose of having logs.

---

### Post by aug7744 on 2021-05-15
Thanks for all replies.
Yes will see the logs.
Have a nice week.

---

