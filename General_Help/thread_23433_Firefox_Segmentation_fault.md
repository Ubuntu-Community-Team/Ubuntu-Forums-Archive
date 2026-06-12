---
title: "Firefox Segmentation fault"
date: 2005-04-01
forum: General Help
---

### Post by dewey on 2005-04-01
I've seen a few other posts on here, but nothing I saw solved my problem, or no one replied.  Everytime I try to run firefox, or mozilla, I get this output.
```
dewey@ubuntu:~$ firefox
Segmentation fault
```

It happened after I installed kubuntu, although it originally worked after the installation, I clicked a link to go to a website I frequent, when it crashed.

All help is greatly appreciated.

[Note:] I installed the hoary preview cd, then apt-getted kubuntu-desktop

---

### Post by dewey on 2005-04-04
Problem solved, I'll post my solution because I know this is quite a popular problem, in all distros.

I used GDB to trace to problem to mozplugger, and removed it.  Instant fix.  I haven't tried to reinstall mozplugger yet, I'll get to that tomorrow.

Hope this helps someone.

---

### Post by mmmkile on 2008-07-08
It had been a long time since this was posted, but I still didn't want my thanks to go unnoticed. So thanks!:)

---

