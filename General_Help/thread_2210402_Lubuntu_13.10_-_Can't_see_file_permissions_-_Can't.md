---
title: "Lubuntu 13.10 - Can't see file permissions - Can't access"
date: 2014-03-10
forum: General Help
---

### Post by bjngchn on 2014-03-10
Lubuntu 13.10 with fde was installed, after some pain and luck. .... From time to time there are errors, for example files can't be accessed because a program fails; but such problems usually disappear once computer restarts. .........PROBLEM: Had trouble deleting files in a directory ,  and also file permissions were unchangeable. So changed (or tried to change) file and direcory permissions to 777 . Also made this  user an admin.  Also tried to fix this from a different user which is admin. ....What to expect: All files should be accessable by everyone. BUT what really what happened: All those directories and files can't be accessd by anyone now even after restarting the computer. Moreover there is still  no file permission info on Dolphin for these directories/files. For other files (untouched ones, newly created ones) there is no such problem.

---

### Post by bjngchn on 2014-03-10
Fixed with "advanced permissions".

---

### Post by mörgæs on 2014-03-10
Good, please mark the thread 'solved'.

---

### Post by bjngchn on 2014-03-10
Not solved yet. Can access directories/files now, they appear to have 777 permission, but those permissions are not changeable unless I use advanced permissions, maybe because of file ownership information. How can we change file ownership info? Main problem now: Can't delete files. But there might be other related problems I'm not aware of.

---

### Post by ajgreeny on 2014-03-10
Let's see the output of ```
ls -la -R /home/*user*
``` then copy the output back here to see if everything in your home is yours.

Or you could simply run ```
sudo chown -R *user*:*user* /home/*user*
``` to make sure everything in your home belongs to you, as it should.

Use your own username in those commands where I wrote "user".

---

### Post by bjngchn on 2014-03-10
Great, last command works.

---

