---
title: "how to dissable X"
date: 2008-02-11
forum: General Help
---

### Post by mfaust731 on 2008-02-11
Hey Everybody,

I have a multipurpose server set up running 7.10, desktop version. I would like to set it up where it does not load x windows or gnome by default on a local connection, but have it available if needed.
I would like it available on a remote connection also.

Also I have been connecting to via with tightvnc, and it seems to be a very laggy setup.
Is there a better way. I m connected with hardwired ethernet and should have a much better connection. I think it may just be the software slowing it down.

thanks for the help

---

### Post by y-lee on 2008-02-11
System --> Administration -> Services

Scroll down and un-check "Graphical Login manager" should prevent it from starting up. I think never tried anything that.

---

### Post by mfaust731 on 2008-02-11
thanks, I found a program called bum (boot up manager) which did the job.
apt-get install bum

thanks

---

