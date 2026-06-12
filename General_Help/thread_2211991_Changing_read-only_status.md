---
title: "Changing read-only status"
date: 2014-03-18
forum: General Help
---

### Post by bjngchn on 2014-03-18
This is about a problem I marked as solved; but I realized it was not completely solved. Two directories with files under /home/user2 became unaccessible by user2 because of encrytiption+mounting problem. One of these directories became accessible after sudo ecryptfs-recover-private and mounted at /tmp/ecryptfs.****** . Other problematic directory can't be accessed in the same way. All chmod values are forbidden (000). Ownership belongs to user2 (in a previous attempt it was root).  So I own a directory, but I can't change its permissions. Reason: Read-Only file system.  Admin. owner, root, sudoer, noone can change its permissions because it is read-only.  Can anything be done about this? Another related problem: A big unaccessible directory under home was deleted, and deleted from trash. But it still occupies lots of space. Where did it go?

---

### Post by Dave_L on 2014-03-18
Was the read-only directory mounted at /tmp/ecryptfs.****** by ecryptfs-recover-private? If so, did you specify the  --rw parameter to mount it read-write?

---

### Post by bjngchn on 2014-03-19
First question answer is yes. second question, answer is no. Why and how use --rw ?

---

### Post by Dave_L on 2014-03-19
By default, ecryptfs-recover-private mounts the recovered directory read-only. If you want it mounted read-write, so you can make changes, you have to specify the --rw parameter.
```
sudo ecryptfs-recover-private --rw [encrypted private dir]
```
[http://manpages.ubuntu.com/manpages/precise/en/man1/ecryptfs-recover-private.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/ecryptfs-recover-private.1.html)

But maybe I misunderstood your problem.

---

### Post by bjngchn on 2014-03-19
Thanks. It works. Half of the problem solved at least. Probably deleting files and emptying trash will be possible after this.

---

