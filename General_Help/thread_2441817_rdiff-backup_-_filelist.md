---
title: "rdiff-backup - filelist"
date: 2020-04-27
forum: General Help
---

### Post by Quarkrad on 2020-04-27
I'm struggling with the filelist you can use with rdiff-backup.  There is lots of information on the filelist including the man pages but where is it located?  if in the terminal you type **rdiff-backup --include-filelist dir1 dir2**  then where is the filelist located that this command refers to?  If you wrote a simple bash script (say script is located in /user/local/bin  that looked something like:

```
#!/bin/bash
rdiff-backup --include-filelist --exclude ~/'**'  ~/ /media/username/backup
```

where is the filelist located?

---

### Post by Quarkrad on 2020-04-27
Doh - it appears to include-list (or exclude-list) has to be in the same directory as the command.  So ... if using the terminal in your home directory then the include-list would be located in your home directory. If, in my example above, the bash script is located in /usr/local/bin then the include-list is also located in /usr/local/bin.  I will leave this un-solved for a few days in case I'm corrected and/or better information is posted.

---

