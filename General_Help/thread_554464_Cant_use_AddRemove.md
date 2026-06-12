---
title: "Cant use Add/Remove"
date: 2007-09-19
forum: General Help
---

### Post by RetroDemon on 2007-09-19
I tried installing Sun-Java5-bin version 1.5.0-11-lubuntu2 and Sun-java5-jre. I couldnt get it to work, but now both the files are sitting in the update manager and wont leave, this is making it so I cant download anything from the Add/Remove thing. How do i get these two files out of the update Manager que!?!?!

When i tell it to update i get this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I just want it to go away, off of my computer!!!

---

### Post by forestpixie on 2007-09-19
it's telling you what to do - run this in terminal

```
sudo dpkg --configure -a
```

you probably need to be using the Abs Beg forum :)

---

### Post by RetroDemon on 2007-09-19
omg, i been at this all day, and you just fixed everything, lol. im such a newb and an idiot.

---

### Post by forestpixie on 2007-09-19
> im such a newb and an idiot

Welcome to you, I've only been here since May myself and I don't for one minute think you're an idiot, and there are no stupid questions before you ask :)

Another thing to learn today is - use thread tools at the top and mark thread as solved.

---

