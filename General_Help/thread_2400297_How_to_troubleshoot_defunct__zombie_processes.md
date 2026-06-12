---
title: "How to troubleshoot defunct / zombie processes?"
date: 2018-09-04
forum: General Help
---

### Post by suaro on 2018-09-04
I've done some research but unable to find anything helpful on how to isolate the parent process or task resulting in thousands of zombie processes?
For example, I have a Ubuntu 16.04 LTS /w latest patches and I see **65,347 ** zombie processes that look like this:

            [systemctl] <defunct>

The system is 4 cores and the machine is running very slow.  Uptime shows > 1600% for all avgs. 

I can reboot the system and it will be fine for maybe 15 days , but gradually gets back into this state. 

How can I determine why these are happening?  They must be originating from systemctl (over and over ) but unsure how to tie these back to the source?
Any troubleshooting tips / tricks would be greatly appreciated.

---

### Post by Bashing-om on 2018-09-04
suaro; Hello -

Maybe a pointer in the right direction. pstree -
[http://askubuntu.com/questions/111422/how-to-find-zombie-process](http://askubuntu.com/questions/111422/how-to-find-zombie-process)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

