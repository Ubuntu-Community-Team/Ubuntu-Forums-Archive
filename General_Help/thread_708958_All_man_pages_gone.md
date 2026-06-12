---
title: "All man pages gone?"
date: 2008-02-26
forum: General Help
---

### Post by ridetheteapot on 2008-02-26
During the recent update of some english language packages, all my man pages are gone, or inaccessible. During the update i had an error occur, but i tried again and it rolled through.
Now my man entries are gone! I installed one package afterwards before i noticed and its manuel is all i can access. Its in /usr/share/man/man1 , and its the only file in there.
Is there another directory and my paths got switched some how? Or has everything een erased somehow?


---EDIT

I dunno if the update caused it or not, but the time frame they went missing is around the same time.
and i dunno what that error was that occurred during the update.... I have a desktop running ubuntu as well that went through the update with no error and the pages are still there.
Really need to know what happened, and if they are gone whats the easiest way to get them back without reinstalling everything?

p.s for sympathy lemme tell you that i was looking for the sed manual when i noticed this

---

### Post by dcstar on 2008-02-27
> **ridetheteapot said:**
> During the recent update of some english language packages, all my man pages are gone, or inaccessible. During the update i had an error occur, but i tried again and it rolled through.
Now my man entries are gone! I installed one package afterwards before i noticed and its manuel is all i can access. Its in /usr/share/man/man1 , and its the only file in there.
Is there another directory and my paths got switched some how? Or has everything een erased somehow?


---EDIT

I dunno if the update caused it or not, but the time frame they went missing is around the same time.
and i dunno what that error was that occurred during the update.... I have a desktop running ubuntu as well that went through the update with no error and the pages are still there.
Really need to know what happened, and if they are gone whats the easiest way to get them back without reinstalling everything?

p.s for sympathy lemme tell you that i was looking for the sed manual when i noticed this

Try this:

**```
sudo mandb
```**

---

### Post by ridetheteapot on 2008-02-27
thanks for the info, didnt seem to get them all back for me though

To be honest i had already copied the man pages from my desktop machine (not all the same, and lots of broken links for the man pages in wierd directories)

i did get this error 
mandb: can't update index cache /var/cache/man/oldlocal/index.db: No such file or directory
and also for /var/cache/man/local/index.db:

but most of the important pages i got of my other machine. but i mandb didnt get anything new for me... ie. i have pan installed on this laptop, and not the desktop(where i copied my man pages from) and i still don't have a man page for pan
but mandb did get rid of the broken links for me ;)

---

