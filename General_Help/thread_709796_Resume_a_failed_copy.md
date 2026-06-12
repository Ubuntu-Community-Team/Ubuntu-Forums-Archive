---
title: "Resume a failed copy"
date: 2008-02-27
forum: General Help
---

### Post by Dooley on 2008-02-27
Does anyone know of a way (preferably via CLI) to resume a failed cp.

---

### Post by Mr. C. on 2008-02-27
If cp fails, you must restart it; there is no checksumming or restart behavior in cp.

MrC

---

### Post by Dooley on 2008-02-27
Is there no other tool that does this?

It didn't seem like cp had this functionality built in.

I have heard of something called extended cp, and it does have resume support, has anyone used this having looked at the manual the only resume support seems to be for one file and only over ftp but I could be very wrong.

Also if someone had a quick script that could recurse through folder,check if a file exists, if it doesnt copy over, if it does check filesizes of all src and dest file and if different overwrite that would be great! Just need something simple that works.

---

### Post by Mr. C. on 2008-02-27
```
man rsync
```

MrC

---

### Post by abulmagd on 2008-05-19
[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-resume-failed-copy-cp-command-where-it-left-off-183092/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-resume-failed-copy-cp-command-where-it-left-off-183092/)

---

