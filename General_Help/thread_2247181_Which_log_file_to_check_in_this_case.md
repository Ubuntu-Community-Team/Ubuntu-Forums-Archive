---
title: "Which log file to check in this case?"
date: 2014-10-06
forum: General Help
---

### Post by sim085 on 2014-10-06
Hello, 

I have installed ubuntu server on a machine. I access this machine through ssh (putty). Last night there was a power cut. When power was restored I turned the machine on. However - even though visibly the machine looked on - I could not login through ssh. I turned off the machine, moved it to my desk (where I have a monitor) and turned it on again to see what is wrong. However it booted just fine and I can connect with SSH.

Is there a log file I can look into to see what might have gone wrong on that last start up? I looked in /var/log/syslog but I did not find an entry for the time when this happened.

---

### Post by JKyleOKC on 2014-10-06
Did you also try /var/log/syslog.1? In my systems, each time the cron.daily job runs, the syslog is rotated by one day and a new file started. Thus the .1 or .2 copies might have the time period you need. You might also look in the /var/log/kern* files...

---

### Post by nerdtron on 2014-10-06
> However - even though visibly the machine looked on - I could not login through ssh.
Did you waited longer before your connected a monitor? Maybe the server was performing a file system check due to the power cut you experienced.

---

### Post by sim085 on 2014-10-06
I turned it off (as I did not have a monitor where the server was located). Strange enough I cannot find any entries in those two files for the time in question. Could it be that because of power cut (maybe motherboard or power supply issue) PC entered in some inconsistent state and never booted? (therefore no logs)

---

### Post by nerdtron on 2014-10-06
Nope. Even with kernel panic, there would still be logs, or at the least, there would be logs starting on what happened before bootup.
What are the files in you /var/log folder?

---

