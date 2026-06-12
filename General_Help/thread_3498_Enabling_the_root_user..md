---
title: "Enabling the root user."
date: 2004-11-06
forum: General Help
---

### Post by tvlad on 2004-11-06
How could i do that ? i looked through /etc/passwd and groups and i see nothing wrong, though i can't login with it when Ubuntu starts.

When i do useradd -o -u 0 -g 0 -d /home/phoenix phoenix, shouldn't it also create /home/phoenix as the home dir ? i tried to create it manually, but even then, it creates no bash.rc there, i think i forgot to add another flag to the option.

And i know root isn't the safest way to do things, but i don't want to sudo all the time, because i really like playing around with the system, and most of the time i know what i'm doing, and even if i brake smth, that's the best way to learn.

---

### Post by im_ka on 2004-11-06
check post #2 in [this](http://www.ubuntuforums.org/showthread.php?t=3396) thread.

---

### Post by jdong on 2004-11-06
To answer your second question, refer to the man page for useradd. The -m option copies over a template /home.

---

