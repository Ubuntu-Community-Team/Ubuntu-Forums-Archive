---
title: "mysqld_safe high cpu load"
date: 2007-03-28
forum: General Help
---

### Post by theaxis69 on 2007-03-28
I just went through the MythTV install and setup.  Everything there is fine.  The problem I'm having is the mysqld_safe process is taking up all spare cpu cycles.  I haven't changed any of the mysql settings, just went through the standard install of mythtv and associated packages through synaptic.  Any ideas?  This is on 7.04 with mysql 5

---

### Post by theaxis69 on 2007-03-28
I should add that the mysqld_safe process takes up all spare CPU cycles whether I'm running the MythTV Frontend or not.  There should be nothing using mysql on my system until I start MythTV.  mysqld_safe just wants to grab as much CPU time as it can, even when it doesn't need it and should be sleeping.

---

### Post by Oukan on 2008-03-28
Edit: Ugh, sorry, saw "March 28" and didn't process "2007", sorry for resurrecting such an old post.

Original:

I had the same problem when I updated today on my Hardy server.  The problem seems to be with the mysqld_safe script not handling stops/starts (e.g. /etc/init.d/mysql stop) of mysql very well.  Info I've found has suggested just force killing the mysqld_safe process (however many times, typically one or two) after stopping mysql and then starting mysql again.  Since my server is just for private testing I just rebooted the whole thing to make it go away and make sure mysql was running properly.  Note that anytime mysql is updated the update will stop and start mysql, thus if the script isn't improved/fixed the same problem will occur again at that time.  Since reboot CPU usage has been normal, though I haven't tried stopping the mysql server either...

---

