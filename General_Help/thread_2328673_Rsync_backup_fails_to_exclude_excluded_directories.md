---
title: "Rsync backup fails to exclude excluded directories."
date: 2016-06-23
forum: General Help
---

### Post by Patrick_Jeeves on 2016-06-23
Hello,

I'm trying to run this backup script:

> 
#!/bin/sh

rsync -aAHXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*", "/etc/fstab","/lost+found", "/home/*/.cache/*"} / /mnt/Backup


But when i ran it it started copying data from the .cache, the lost+found, the fstab file got replaced, and then it started to copy in the backup drive itself getting into an infinite loop until I stopped it with ^C.  What am I doing wrong?

---

### Post by SeijiSensei on 2016-06-23
I think the quotation marks might be a problem.  Try putting all the excludes in a file and use "--exclude-from=filename".  Something like this:
```

/proc/
/sys/

```
I also think you can get rid of most of the asterisks.  Use "/proc/" rather than "/proc/*".

---

### Post by Patrick_Jeeves on 2016-06-23
Didn't work. It still copies all of them.

---

### Post by &amp;KyT$0P# on 2016-06-23
First off, I agree with SeijiSensei that the wildcarding you're using is going to cause you issues.  That needs to be tweaked slightly.
Try also using one --exclude= per exclude, and using single-quotes in the shell?

So it would look like:
```
#!/bin/sh

rsync --dry-run -aAHXv --exclude='/mnt/Backup/' --exclude='/dev/' --exclude='/proc/' --exclude='/sys/' --exclude='/tmp/' --exclude='/run/' --exclude='/mnt/' --exclude='/media/' --exclude='/etc/fstab' --exclude='lost+found/' --exclude='/home/*/.cache/***' / /mnt/Backup
```
(Added --dry-run option for testing, so that if it doesn't work it won't risk to destroy your data.  **Do not remove --dry-run until you are 100% sure it works exactly like you want.**)

Does this help?

---

### Post by Patrick_Jeeves on 2016-06-23
Yes that fixed it, thank you very much!

---

### Post by &amp;KyT$0P# on 2016-06-23
You're welcome! :D

---

### Post by oldrocker99 on 2016-06-23
In the problem is solved, and it appears to have been, please add [SOLVED] to the thread title.

Thanks.

---

