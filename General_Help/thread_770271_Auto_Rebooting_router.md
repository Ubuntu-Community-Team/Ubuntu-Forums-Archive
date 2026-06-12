---
title: "Auto Rebooting router"
date: 2008-04-27
forum: General Help
---

### Post by ozdesi on 2008-04-27
Hi All,

I have been using Telenet script in Windows to schedule a router reboot to comply with my ISPs rules for Night Unlimited Usage. This way I can log out and log in from broadband connection at a specific time.

For this purpose I need Windows Scheduler and [Telnet Scripting Tool]("http://www.winsite.com/bin/Info?500000000873") 

Does anyone know how to run similar programs in Ubuntu?

---

### Post by jocko on 2008-04-27
I'm not sure if this will help you or not, but telnet is available as a command line tool (just type "telnet" or "telnet [address to connect to]" in a terminal.
More info if you type "man telnet" in a terminal. 
If you need a graphical telnet client, there may be some avalable in the repos (e.g. putty).

For scheduling tasks, I think you could use cron (aready installed by default).
I have no idea how to schedule a task in cron, so I guess you'll have to search for it...

---

