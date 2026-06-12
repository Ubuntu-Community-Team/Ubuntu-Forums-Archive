---
title: "How to save (and restore) package management/application data?"
date: 2019-04-13
forum: General Help
---

### Post by ATSC on 2019-04-13
Hi :-)


the hd where my system is on is broken - I can access it only via a  live-cd. How do I save the necessary package/software installation data  (package list, extended package-data? key rings? software manager data?  etc...?) from within the live-cd?


cheers

---

### Post by TheFu on 2019-04-13
All of this is easy to do, BEFORE there are issues.

All I can suggest at this point is that you backup everything in /etc/ and /home/
That won't get installed packages.  Normally, I'd use **apt-mark showmanual** to get the list of manually installed packages and save those to a file. On a broken system, I don't think that will work without lots of manual steps and with a failing HDD, there's no telling which parts of the OS are toast/not working.

Backups are best made BEFORE any issues happen. There are thousands of different methods to make backups on a working system using about 50 different tools.

Sorry I'm not of more help.

---

