---
title: "Is this a tar error, or just a different exit code?"
date: 2008-04-07
forum: General Help
---

### Post by xelapond on 2008-04-07
I have a 16 gig .tar file that is a backup.  I am moving it to another drive, but cp will not copy the file(says maximum file size error).  I decided to untar it to a folder, because its actually smaller that way.  When I ran tar -xvf ./Backup.tar is displayed the following output at the end:

tar: Error exit delayed  from previous errors

What does this mean?

---

### Post by phidia on 2008-04-07
Take a look at [this]("http://www.linuxquestions.org/questions/linux-software-2/tar-error-exit-delayed-from-previous-errors-using-c-629147/?highlight=tar%3A+Error+exit+delayed+from+previous+errors") from linuxquestions and see if that's the issue.

---

### Post by chunchengch on 2008-04-07
try this,

$ sudo tar --exclude=stats/* -czpf ./Backup.tar *

---

