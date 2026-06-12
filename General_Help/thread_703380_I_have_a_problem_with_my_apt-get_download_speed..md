---
title: "I have a problem with my apt-get download speed."
date: 2008-02-21
forum: General Help
---

### Post by Emo_Samurai on 2008-02-21
I'm using gutsy-gibbon, and my apt-get's running really slowly, 21B-15kB. 

Here's my sources.list file:

```


deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security multiverse

deb http://mirror.noreply.org/pub/tor gutsy main
deb-src http://mirror.noreply.org/pub/tor gutsy main



```

---

### Post by Sam Lars on 2008-02-22
I'm not sure that it would matter, but the line that says "multiverse" isn't commented out.
Sometimes I've noticed that it's just slow...

---

