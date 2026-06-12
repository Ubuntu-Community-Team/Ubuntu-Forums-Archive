---
title: "Evolution Memory Leak"
date: 2012-12-21
forum: General Help
---

### Post by rocketrrt on 2012-12-21
Hello,

I am new to Linux world

I have Ubuntu Server 12.04 x64 with lubuntu Desktop. I am trying to use evolution 3.2.4 from the software center, taking with exchange server. everything works but evolution is leaking memory at fast rate.  I have seen in 1 day evolution can be using up to 1 GIG of memory that it not releaseing.  Having to shut it down and restart is pain.

Ron

---

### Post by rnerwein on 2012-12-21
> **rocketrrt said:**
> Hello,

I am new to Linux world

I have Ubuntu Server 12.04 x64 with lubuntu Desktop. I am trying to use evolution 3.2.4 from the software center, taking with exchange server. everything works but evolution is leaking memory at fast rate.  I have seen in 1 day evolution can be using up to 1 GIG of memory that it not releaseing.  Having to shut it down and restart is pain.

Ron
hi
hope you are a little bit conform with a terminal.
the way i start when a deamon have a memory leak i will get a core dump from the process (hey that's no joke !).
there is a command named "gcore" on the system. don't be afraid it don't kill the process the process will still run.

in a terminal execute: gcore -o my_core pid_of_the_process  (you must have the permission to attach the process)

then type: strings my_core | more
if you get luck you will see 1000s of strings with the same text. that's the leak. with this info the developer will be able to fix the memory leak very fast ( in a couple of times the error was between my ears)
have luck
cheers

---

