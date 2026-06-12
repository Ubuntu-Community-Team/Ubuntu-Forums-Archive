---
title: "KTorrent error - &quot;too many open files&quot;"
date: 2007-02-18
forum: General Help
---

### Post by srunni on 2007-02-18
Hi,

I use KTorrent, and I've seen recently that if I don't keep the number of torrents running below a certain number (not sure exactly what that number is), I get an error on active torrents saying that too many files are open, and that torrent stops. Does anybody know how I can fix this? Also, does this happen with Azureus? I'm currently running Kubuntu Dapper, but I plan on upgrading directly to Kubuntu Feisty when it's released, and switching to Azureus   as well when I do.

Thanks in advance for the help!!

---

### Post by madberry on 2007-02-21
Hey scrunni,

For application specific information alway surf to the website of the application.......

the link below should point you in the right direction...

[http://ktorrent.org/forum/viewtopic.php?t=1283&highlight=open+files]("http://ktorrent.org/forum/viewtopic.php?t=1283&highlight=open+files")

Greetz,
[mad]Berry

> **srunni said:**
> Hi,

I use KTorrent, and I've seen recently that if I don't keep the number of torrents running below a certain number (not sure exactly what that number is), I get an error on active torrents saying that too many files are open, and that torrent stops. Does anybody know how I can fix this? Also, does this happen with Azureus? I'm currently running Kubuntu Dapper, but I plan on upgrading directly to Kubuntu Feisty when it's released, and switching to Azureus   as well when I do.

Thanks in advance for the help!!

---

### Post by jvbryne on 2007-05-28
Btw; The answer was changing the limit using ulimit. 'sudo ulimit -n 4096' to up the limit from 1024 to 4096 worked for my setup.

---

