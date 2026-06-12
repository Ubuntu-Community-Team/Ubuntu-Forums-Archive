---
title: "Shutdown Errors"
date: 2007-08-20
forum: General Help
---

### Post by Romanus81 on 2007-08-20
Ever since I installed Wubi I have never been able to shut down my system. I even tried using LVPM to put it on it's own partition and didn't have any luck. (I switched back to Wubi because I just felt more comfortable) 
Recently I had to do a hard reboot because my system froze, and everything stopped working, I couldn't enter my session manager, panels started dissapearing, and I got a ton of errors when I tried shutting down.
I decided to start a fresh install, and since, by doing something I can't remember a long time ago, I caused a lot of problems with my windows install I decided to do a system restore to the day before I installed Wubi, cleared the C:/wubi files. I reinstalled Wubi, redownloaded the iso and made a fresh install.
I updated the system, and when I shutdown to restart my computer, I got the same errors. I attatched an image of the errors, I don't know if anyone is familiar with this, or if this is a major problem, but if anyone knows anything about it I would appreciate it.

---

### Post by ago on 2007-08-21
I assume you are using the latest version.

You should have 2 files:

/etc/init.d/fixsendsigs
and
/etc/rc6.d/S10fixsendsigs

If for some reason one of the 2 is missing you cannot reboot

---

### Post by psayre23 on 2007-08-31
So what can we do to fix this? Just find those files online and replace? And is there a particular version we should be looking for?

I have been living with this problem for a few months because I got everything working the way I like. Is there any way to upgrade wubi without reinstalling ubuntu? Maybe save the old vdisks?

---

