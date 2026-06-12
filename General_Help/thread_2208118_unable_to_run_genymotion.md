---
title: "unable to run genymotion"
date: 2014-02-26
forum: General Help
---

### Post by jrmchess on 2014-02-26
whenever I run genymotion I get this error > Installing log handler
Logging activities to file: /home/johar/.Genymobile/genymotion.log
Aborted (core dumped)


I went through this link [http://scriptogr.am/dzinek/post/genymotion-qt-gentoo](http://scriptogr.am/dzinek/post/genymotion-qt-gentoo) for a fix and found this solution > So, there is simple solution - rename all libQt*.so.4 files to libQt*.so.4.old and make symlinks for all of them from /usr/lib/qt4 directory. and hence renamed all qtlib files with a .old suffix but I don't know how to create symlinks for those files from this directory /usr/lib/qt4 as I can't find any qtlib files there.

Can someone pls help? Thanks

---

### Post by jrmchess on 2014-02-27
somebody please help!

---

