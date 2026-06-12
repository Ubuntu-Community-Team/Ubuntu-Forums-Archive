---
title: "Backup tool with webinterface"
date: 2007-08-16
forum: General Help
---

### Post by snorhyvel on 2007-08-16
hi all, I need a backup tool that is easy to handle for an unexperienced user preferably via a web interface.

---

### Post by PaulFr on 2007-08-17
Some suggestions:

1. Simple Backup Suite **[B][https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)**

2. Bacula (has a Web interface) **[http://www.bacula.org/](http://www.bacula.org/)**

3. Amanda (little more complex) **[http://amanda.zmanda.com](http://amanda.zmanda.com)**

Overall view of backup is at **[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)**.

---

### Post by HermanAB on 2007-08-17
Well, a backup tool is something you set and forget, so a web interface is not particularly useful.  On Unix systems backup is typically scripted and then hooked to cron.daily so it runs in the middle of the night.  So, you would probably be better served to read the rsynch and ssh man pages, than to try and get a fancy web interface to work that will not ever be used.

---

