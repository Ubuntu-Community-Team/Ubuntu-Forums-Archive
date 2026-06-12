---
title: "[SOLVED] /dev/sda2 UNEXPECTED INCOSISTANCY; RUN fsck manually"
date: 2008-07-04
forum: General Help
---

### Post by morbid_bean on 2008-07-04
booted up my box and this "routine check of drives" thing shows up...if i allow it to check it will come to this screen where i get some crap like "/dev/sda2 UNEXPECTED INCOSISTANCY; RUN fsck manually"   and wont boot...

lol help?

---

### Post by Herman on 2008-07-04
Boot your Ubuntu 'Desktop' Live/Installation CD and open a terminal and run:
```
sudo e2fsck -C0 -f -p -v /dev/sda2
```That should fix it or if it can't, it will give you an error message with a clue about what to try next.

---

### Post by morbid_bean on 2008-07-04
> **Herman said:**
> Boot your Ubuntu 'Desktop' Live/Installation CD and open a terminal and run:
```
sudo e2fsck -C0 -f -p -v /dev/sda2
```That should fix it or if it can't, it will give you an error message with a clue about what to try next.

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -p -v /dev/sda2
/dev/sda2: recovering journal
/dev/sda2:                                                                      Deleted inode 671759 has zero dtime.  FIXED.
/dev/sda2:                                                                      Inodes that were part of a corrupted orphan linked list found.  

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
ubuntu@ubuntu:~$ 

```

---

### Post by Herman on 2008-07-04
```
sudo e2fsck -y -f -v /dev/sda2
```I hope you had your data backed up now, because running e2fsck without -a or -p options means there's a high likelyhood that some files will need to be unlinked and you might find them in the /lost+found afterwards.
It is possible to recover some data from /lost+found if you have to, but it is always better to have up to date backups. Depending on your luck it might only be something trivial that gets deleted to the lost+found, or it might be a vital operating system file, so your operating system may or may not be recoverable. 

Good luck!

Regards, Herman

---

### Post by morbid_bean on 2008-07-05
ok got it back and working...thanks alot...now how do I make this Thread SOLVED?


thanks again 	\\:D/

---

### Post by Herman on 2008-07-05
You're welcome. 
I think there's a option in 'thread tools', at the top of the page, but it doesn't show up at my end, maybe it does for the original poster?
Regards, Herman :)

---

