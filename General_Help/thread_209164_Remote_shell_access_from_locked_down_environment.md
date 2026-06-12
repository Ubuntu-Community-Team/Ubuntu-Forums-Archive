---
title: "Remote shell access from locked down environment?"
date: 2006-07-04
forum: General Help
---

### Post by falcon15500 on 2006-07-04
Hello,

  Any ideas on how I can access the shell of my home Ubuntu box, from a locked down (work) environment?  I previously was able to set up a http tunnel through works proxy to my home machine, over which I ran SSH.  However recent proxy modifications at work have stopped this method from working - the initial http tunnel doesn't connect.

  Ethical considerations aside, I don't want to forgo being able to tinker with my setup from work.  I run a web server, which is accessible from work.  Perhaps I could run a java shell client of some sort?

  Any ideas appreciated.

falc

---

### Post by shanet on 2006-07-04
well, I can't tell you how to do it because I've never tried, but there's a secure way of getting virtual ssh on the web through PHP, if you can manage writing a bit of PHP. I have read about it in magazines, but there seems to be a good few resources about it. presumably the solution you are looking for would have to be server-side, because a java shell client would have the same problems with ports that presumably stops you using putty etc, I presume.

---

### Post by falcon15500 on 2006-07-04
Exactly.  I am thinking the solution needs to be server-side.  Have done some googling already, but will do some more from a PHP angle.  Thanks for the tip!

falc

---

### Post by kb2wdi on 2006-07-04
Have you tested port 443 (HTTPS port)?

Change port in "/etc/ssh/sshd_config"

---

### Post by falcon15500 on 2006-07-04
[QUOTE=kb2wdi]Have you tested port 443 (HTTPS port)?

Change port in "/etc/ssh/sshd_config"[/QUOTE]

Are you suggesting I set sshd to listen for ssh connections on port 443?
Unfortunately that port is already in use for my web server.
Thanks for the suggestion though!

falc

---

