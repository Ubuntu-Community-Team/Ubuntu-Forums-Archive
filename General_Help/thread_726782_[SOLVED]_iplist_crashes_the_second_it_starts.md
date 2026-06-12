---
title: "[SOLVED] iplist crashes the second it starts"
date: 2008-03-17
forum: General Help
---

### Post by mandrill on 2008-03-17
Had it up and running fine for quite awhile, then did a fresh install of gutsy and it just won't work. Any ideas? Depencies resolved, got the gutsy deb from sourceforge....


Edit: Packages all install ok. Then when attempting to launch GUI I get a quick flicker in the bottom panel, then nothing. Opened in terminal, and got this:


jim@monkey:~$ sudo ipblock
IPblock 0.19
Copyright (C) 2008 Serkan Sakar <uljanow@users.sourceforge.net>

Usage: ipblock [options]

Options:
 -s     start blocking
 -d     stop blocking
 -r     restart IPblock
 -u     update lists
 -c     convert lists to ipl format
 -g     start IPblock GUI
 -l     show status
 -v     show version and exit
 -h     show this help
jim@monkey:~$ sudo ipblock -s
jim@monkey:~$ sudo ipblock -g (open gui)
exec: 348: java: not found

I have jre6 installed through synaptic.  What gives?

---

### Post by mandrill on 2008-03-17
Bump

---

