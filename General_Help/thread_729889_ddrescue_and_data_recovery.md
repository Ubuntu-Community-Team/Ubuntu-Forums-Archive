---
title: "ddrescue and data recovery"
date: 2008-03-20
forum: General Help
---

### Post by nisarg on 2008-03-20
Some say one shouldnt run ddrescue or any other data recovery tools to on an healthy hard drive too often as a backup tool - and that could affect the disk.
I am not sure? 
Is it a good idea to run ddrescue often - say weekly - to backup the entire disk? If running often is not a good practice, can it be run occasionally to take a complete backup?
I think its a good tool - fast, and the ability to copy the entire disk in a go, stop and resume copying.. what else do you really ask for a backup tool I say !!
Comments?

---

### Post by ruy_lopez on 2008-03-20
> **nisarg said:**
> I think its a good tool - fast, and the ability to copy the entire disk in a go, stop and resume copying.. what else do you really ask for a backup tool I say !!
Comments?

What else do I ask of a backup tool? Incremental backups. Copying the entire disk every time something changes is inefficient. Plus dd images can only be restored to an identical device, unless you mount them using a loopback, in which case you might as well have used tar, since you'll be restoring by hand.

rsync meets most of my needs

---

