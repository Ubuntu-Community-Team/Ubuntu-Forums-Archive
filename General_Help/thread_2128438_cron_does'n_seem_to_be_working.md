---
title: "cron does'n seem to be working"
date: 2013-03-23
forum: General Help
---

### Post by qvasic on 2013-03-23
I just got Ubuntu Server running, for testing purposes I have added just one line to my crontab (using crontab -e):

*/1 * * * * touch ~user/test/out

Nothing seem to be happening.
I have added all rights for everybody for test directory - nothing changed.

What can it be?

Thanks.

---

### Post by Toz on 2013-03-23
Hello and welcome to the forums.

> ~user/test/out

^^^This doesn't look right. Is it a valid location in your filesystem? Do you mean:

```
~/test/out
```
...or
```
~/user/test/out
```
...instead?

You should also get in the habit of specifying full paths to directories/files and not use shortcuts in cron:
```
/home/user/test/out
```

---

### Post by qvasic on 2013-03-23
> **Toz said:**
> Hello and welcome to the forums.
^^^This doesn't look right. Is it a valid location in your filesystem?
No it isn't: user is a substitution for my username on the system.
In crontab itself there is right username and thus location in the filesystem is valid.

> **Toz said:**
> You should also get in the habit of specifying full paths to directories/files and not use shortcuts in cron:
```
/home/user/test/out
```
Why?

---

### Post by qvasic on 2013-03-23
> **Toz said:**
> Is it a valid location in your filesystem?

Oops, look like it isn't: I have used my login name from other Unix system I use for year now, thus I wan't able to catch it.
Excuse me for distracting you.

---

