---
title: "Linux robust copy command?"
date: 2007-12-30
forum: General Help
---

### Post by Alhazred on 2007-12-30
Hi all.

Does anyone know of a linux command line copy utility that is more or less the equivalent of robocopy.exe? I frequently have need to copy files between computers on my home lan, and usually just use the cp command.

Trouble is, sometimes (more often than I like!) I need to reboot my cable router to restore internet connectivity. So it would be nice to be able to have the file copy be automatically restartable, and to pick up where it left off. It would also be nice to have some sort of simple display indicating the estimated completion.

Thanks in advance.

Mick

---

### Post by icheyne on 2007-12-30
rsync -a --delete

---

### Post by HermanAB on 2007-12-30
rsync, unison, lftp, wget, nc, scp to name a few.

Cheers,

Herman

---

### Post by dagnabit dang doohickey on 2007-12-30
```
rsync --partial --progress *source* *target*
```
Check out the man page for rsync for options aplenty.

---

### Post by Alhazred on 2007-12-31
Thanks for all the replies, guys. I have much happy manual reading ahead of me.

---

