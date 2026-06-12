---
title: "repeat a command ever 5mins?"
date: 2007-09-12
forum: General Help
---

### Post by notjohn101 on 2007-09-12
is there a way to make the computer execute a command ever 5 mins or so

so it keeps my video card at the right clock

---

### Post by psusi on 2007-09-12
Huh?  If you use a tool to change the clock speed on your video card, it shouldn't change again unless you run the tool again to change it. 

To answer your question though, you can use cron to automatically run background jobs on a schedule ( man cron ) or you can use a shell loop command to run until you decide to ctrl-c it:

while true ; do somecommand ; sleep 300 ; done

---

### Post by energiya on 2007-09-12
using cron: "crontab -e" and add
*/5 * * * * /command/to/execute

---

### Post by notjohn101 on 2007-09-12
> Huh? If you use a tool to change the clock speed on your video card, it shouldn't change again unless you run the tool again to change it.

To answer your question though, you can use cron to automatically run background jobs on a schedule ( man cron ) or you can use a shell loop command to run until you decide to ctrl-c it:

while true ; do somecommand ; sleep 300 ; done

well my video card changes clock when it goes from 3d to 2d mode...yea its werd i i no

but thanks for the help

---

