---
title: "Having troubles rebooting amuleweb with monit..."
date: 2013-10-09
forum: General Help
---

### Post by AlejandroVillamarin on 2013-10-09
Hi there!

I'm trying to setup monit to start amuleweb each time it goes down...something that happens quite often I'm afraid. I already have a monit rule for amule-daemon that works really fine, but the one for amuleweb does not...

Here is my section in monit related to amuleweb

check process amuleweb
matching "amuleweb"
start program = "/usr/bin/amuleweb"
stop program = "/usr/bin/amuleweb"

The path is correct and monit is running, but it does not start amuleweb when it goes down...I've tought in creating a simple python or bash script to do this...but it seems overkill having monit...

Any ideas?

Thank you!

---

