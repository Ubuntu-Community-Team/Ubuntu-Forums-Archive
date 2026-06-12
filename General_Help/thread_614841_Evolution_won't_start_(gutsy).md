---
title: "Evolution won't start (gutsy)"
date: 2007-11-16
forum: General Help
---

### Post by hughh on 2007-11-16
When I try to start Evolution from a panel icon, I get the audible signal that it's starting, but nothing appears on my screen.  

When I try to start Evolution from the command line, I get the following:
> 
hugh@Ubuntu:~$ evolution --component=mail
CalDAV Eplugin starting up ...
I've waited for anything else to happen for 30 minutes, but it never does.

I can't find anything relevant in any log file.

Help!

---

### Post by hughh on 2007-11-16
Rebooting the system solved this problem.  Note that logging out of Gnome and back in was *not* sufficient to solve the problem.

---

