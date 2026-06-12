---
title: "Ubuntu 16.04 Krusader doesn't store FTP passwords"
date: 2017-02-20
forum: General Help
---

### Post by gelembjuk2 on 2017-02-20
Hello,
Since i migrated to Ubuntu 16.04 , Krusader doesn't have an option to remember FTP passwords.
My migration was just clean install. On previous versions there was no problems with Krusader.

When i add new FTP tab there is no option "Remember password" on auth dialog. I have to enter a password for each session. 

Other KDE applications are fine (i use kate editor and it saves passwords fine for ftp hosts)

What can be the reason? Any ideas how to fix this?

---

### Post by mastablasta on 2017-02-20
post a bug to Krusader developers.: [https://krusader.org/report-bugs/](https://krusader.org/report-bugs/)

otherwise i use filezilla for FTP and use keys and sFTP protocol instead of passwords. of course keys are not always possible (e.g. no option of sFTP at host). but passwords work well in Filezilla.

hard to say what your issue is. perhaps you need to purge krusader and reinstall it. maybe they changed settings in newer version and they didn't load as it saw the old ones or something.

---

