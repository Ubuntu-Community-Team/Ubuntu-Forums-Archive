---
title: "usplash problem"
date: 2007-05-11
forum: General Help
---

### Post by Saiedt on 2007-05-11
please guide me to solve my problem with usplash. we are working on a
Linux distribution based on ubuntu.
when we boot system from CD after pressing ENTER usplash appears (with
another theme) and progress bar starts to move but after a while usplash
will be dissappeared  or hide and text boot log messages appear on screen.
this the my problem that these log messages must not appear or if appear,
log on background and usplash must not hide at all. I have not any problem
on our desktop computers but on laptops this problem exists.
I think the source of this problem is that kernel or initscripts log
messages will show on same tty that usplash runs and I think if we can
reject or redirect log messages to another tty the problem solves.

any comment or guide strongly appreciated

---

### Post by vav on 2007-05-11
Usually that happens when some task is taking too long... try disabling the quiet option while booting and see which step is taking too long. Sometimes it's starting networking, sometimes it's running fsck on root partition...

---

### Post by Saiedt on 2007-05-12
the last message in usplash is :
Configuring X... 
and after that usplash hides. how can i disable it?

---

