---
title: "Postfix not starting"
date: 2008-05-01
forum: General Help
---

### Post by awacs on 2008-05-01
On a new 7.10 server install, Postfix will not start at boot. Message displayed:

* Starting Postfix Mail Transport Agent

then

postfix/postfix-script: fatal: Usage: /etc/init.d/postfix {start|stop|restart|reload|flush|check|abort|force-reload}

Starting Postfix from the command line:
# postfix start 
works, however

# /etc/rc3.d/S20postfix start
doesn't.

Can any shell scripting wizards figure out where the script (attached) is broken?

---

### Post by supradave on 2009-03-05
Sorry for the delayed response.  I just diagnosed this on my machine and it appears that the rc2.d/S20postfix is trying to start before the S28NetworkManager.  S20postfix is the default.  Therefore:

update-rc.d -f postfix remove
update-rc.d postfix defaults 30

That'll start it after the network.

---

