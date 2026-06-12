---
title: "Rsync + tar.gz"
date: 2015-08-30
forum: General Help
---

### Post by dsx2 on 2015-08-30
Hi 

Trying to make a backup, I was wondering if it's possible to rsync to an external drive directly to an archive tar.gz, tar.bz2 or tar.7z ??

rsync is unable to make a incremental backup if it's more than a file in an archive.

Anyone can think about a way to do so ?

---

### Post by SeijiSensei on 2015-08-30
Not that I know of.  But you could write a simple script that uses rsync to copy things to a directory on the backup server, then runs tar to archive the directory.

---

### Post by dsx2 on 2015-08-30
yes I though about a script to do so, the think is we will end up with two directories  then, and the purpose of this is to save space and make a backup .

---

### Post by SeijiSensei on 2015-08-30
Have the script delete the directory after the tar file is created.

---

### Post by dsx2 on 2015-08-30
Yeah very good idea a script who open the archive sync everything rezip it then put everything in order !! 
Thanks !
I'll post the script as I get it done !!

---

