---
title: "How to restore data on /home/user accidentally removed"
date: 2007-11-14
forum: General Help
---

### Post by satimis on 2007-11-14
Hi folks,


Ubuntu 7.04 server amd64


While I login as "satimis", I accidentally ran "sudo deluser --remove-all-files satimis" removing all data and config files of "satimis".  Because login, "satimis" and its home directory /home/satimis are still there after relogin.  I'm trying to restore the backup.  I never did it before.


googling brought me following thread;
home user backup/restore problem 
[http://ubuntuforums.org/showthread.php?t=546905](http://ubuntuforums.org/showthread.php?t=546905)

$ apt-cache policy dar```

dar:
  Installed: (none)
  Candidate: 2.3.3-0ubuntu1
  Version table:
     2.3.3-0ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages

```
dar NOT installed.  I'll install it later.


Please advise;

1)
Where is /path/my_archive_file?  How to find it?

2)
Currently I have some working data on /home/satimis copied from another PC with "scp".  Will restore overwrite those working data?  If YES, can I move them to another user's home for temporary storage?

3)
Are there better solutions than that mentioned on the above thread?


TIA


B.R.
satimims

---

