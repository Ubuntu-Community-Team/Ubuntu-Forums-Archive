---
title: "Sigh... One Last Time With Postfix"
date: 2005-09-13
forum: General Help
---

### Post by megamartianca on 2005-09-13
Alright, I've given up on the idea of using the Debian test package for Postfix 2.2, and have decided to give compiling from source a try.  The question I have is how do I tell Ubuntu that there is a mail server.  Anacron, at least, requires this, and I need to have a cron daemon running.  Does anybody have an idea as to how I integrate a custom-compiled mail server into Ubuntu?

---

### Post by KenLazlo on 2005-09-13
postfix is startet as a system service, not by cron. 

when the default postfix package is installed, there is a start script /etc/init.d/postfix 

maybe you can make a copy of this script. 

see also the links to this file in /etc/rc1.d /etc/rc2.d etc. 
They start or stop postfix in different runlevels (1,2,3 etc.)

---

