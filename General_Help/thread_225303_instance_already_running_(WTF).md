---
title: "instance already running (WTF?)"
date: 2006-07-29
forum: General Help
---

### Post by Bou on 2006-07-29
Hi, I'm trying to start amule but I get this message:

> Initialising aMule
Checking if there is an instance already running...
There is an instance of aMule already running
Raising current running instance.

There's no instance of amule, though:

> david@david-laptop:~$ killall amule
amule: no process killed

So, what could I do to get amule up & running again?

Thanks in advance!

---

### Post by T700 on 2006-07-29
I've seen a locked file give that same error.  You might try logging out of the session and logging back in.  

Paul

---

### Post by doc_holiday on 2006-08-16
I have the same error, even after reboot the problem remains.

---

### Post by editrix on 2006-08-16
**WARNING** I don't use amule, so this may not be relevant, but ...

I occasionally have the same problem with Kmail and lock files. The lock file should unlock when you shut down, but sometimes it doesn't. Try renaming the lock file to something like lockDATE_OF_THE_FILE and see if that helps. If it doesn't, you can remove the DATE_OF_THE_FILE and at least you won't have screwed anything else up.

---

### Post by jotagab on 2006-08-17
I had the same problem once. aMule just didn't remove the lock file after exiting (crashing?). If I remember correctly the file to remove is ~/.aMule/muleLock

---

### Post by doc_holiday on 2006-08-17
Thank you, that worked

---

### Post by GabrielWolff on 2007-01-13
Works, but I have to remove that mulelock file every time I boot.

How come?

Why does that file appear?

How do I change that setting?

Gabriel

---

