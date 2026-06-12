---
title: "startup &amp; shutdown error logs"
date: 2007-08-10
forum: General Help
---

### Post by l5nrr on 2007-08-10
When I start & shut down feisty, a lot of text scrolls up the screen, too fast to read. Is it piped to logfiles somewhere? Where? I can't see anything in /var/log/* that matches the brief glimpses I can see.

---

### Post by kast on 2007-08-10
try looking in

 (System -> Administration -> System log) 

I think you could also use the terminal and issue cat /var/log/messages | more

---

### Post by l5nrr on 2007-08-10
kast
thanks
turns out 
grep  warn   /var/log/*
did the trick.

---

### Post by kast on 2007-08-10
Sweet glad to hear it

---

### Post by flat4 on 2007-08-10
I was looking at my syslog and keep seeing this entry every single day at the same time.

Can some help me decipher why cause the restart?

Aug  7 08:51:02 home-laptop syslogd 1.4.1#20ubuntu4: restart.

---

### Post by kast on 2007-08-11
Does it just suddenly reboot (i.e., hard reboot) or does it act like it is doing a proper shut-down first?

can you post more of the log for us?

---

### Post by flat4 on 2007-08-13
no it  does not do a proper shutdown, it just reboots

I will have to post it later as I have no access to it. I use it to play hold music for my work.

---

