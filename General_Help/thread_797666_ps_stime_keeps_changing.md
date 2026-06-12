---
title: "ps stime keeps changing"
date: 2008-05-17
forum: General Help
---

### Post by danorton on 2008-05-17
The start time (stime) of a process keeps changing each time I run ps.  Any clue why?

e.g below sometimes it's 12:30, other times it's 12:29:

[font=monospace]
UID     PID  PPID  C STIME TTY STAT TIME CMD
postfix 2237 19169 0 12:30 ?   S    0:00 pickup -l -t fifo -u -c

postfix 2237 19169 0 12:29 ?   S    0:00 pickup -l -t fifo -u -c
[/font]

---

