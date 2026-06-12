---
title: "Ubuntu Server Screen: Sorry, could not find a PTY"
date: 2013-12-26
forum: General Help
---

### Post by sslx on 2013-12-26
I'm trying to use screen command on ubuntu server 13.10. However, I can only use it with sudo. Otherwise I get this.
No more PTYs.
Sorry, could not find a PTY.
[screen is terminating]
I already tried the followings, but it didn't work for me.
chmod a+w /dev/ptmx
mount devpts /dev/pts -t devpts -o mode=620
mount: devpts already mounted or /dev/pts busy
mount: according to mtab, none is already mounted on /dev/pts
Can someone help me to fix this? This is a fresh install.

---

