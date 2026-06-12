---
title: "Ubuntu Server /sbin/getty help"
date: 2007-07-03
forum: General Help
---

### Post by coke on 2007-07-03
I just got done installing Ubuntu Server on my laptop.

I've noticed that the login prompt comes up before the system finishes loading. I've searched around in /etc/init.d and all the rc folders but can't find the actual spot where /sbin/getty is getting called for.

I want to make it the last thing that loads. In other words, I want the system to fully load before the login prompt comes up.

Any ideas?


Thanks in advance. This is a great distro for server installations!

---

### Post by coke on 2007-07-03
Just in case anyone was wondering - I figured it out.

It was the different loader that Ubuntu now uses to load system initialization scripts. I issued apt-get install sysvinit and it took care of it.

---

