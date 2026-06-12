---
title: "Pidgin Process Taking CPU in Uninterruptible Sleep"
date: 2008-06-29
forum: General Help
---

### Post by noahl on 2008-06-29
I have a process called 'pidgin' (full command 'pidgin') consistently taking between 75 and 90 percent of my CPU time (according to top), and I can't kill it because it's in uninterruptible sleep (checked the system monitor). I sent every signal in /bin/kill -L to it and it had no effect. The process was started by init. It's distinct from the usual pidgin process, which starts and stops normally. I can't figure out how to get rid of it without restarting, and if I do that, I still won't know how to make sure it doesn't happen again.

---

