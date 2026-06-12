---
title: "Wrong shell for new terminals &amp; screen - X envar?"
date: 2007-06-19
forum: General Help
---

### Post by Mopatop on 2007-06-19
****SOLVED****

Hey guys

I just got back from lunch and now my machine is using the wrong shell when I open new terminals. It's running sh instead of bash (which makes me suspect that it's falling back for some reason), however I can't work out why.

I've done usermod --shell /bin/bash rob and checked /etc/passwd. I've tried different terminals. I get the right shell when I log in from a TTY or over SSH.

Any ideas?

The only thing I can think of is perhaps the SHELL environment variable of my running X session has been changed to /bin/sh - God  knows why. Does anyone know how I change an environment variable of my running X session?

(Yeah I know I could just restart X or my machine but that's not the right solution)

Thanks!

---

### Post by Mopatop on 2007-06-19
NEVERMIND! Got it :-)

My xfdesktop was using loads of memory so I set up a crontab to kill and restart it every hour. Of course, cronjobs execute with SHELL set to /bin/sh, which was being inherited by xfdesktop, which was being inherited by my launched terminals

AAHH!

Sorted now.

---

