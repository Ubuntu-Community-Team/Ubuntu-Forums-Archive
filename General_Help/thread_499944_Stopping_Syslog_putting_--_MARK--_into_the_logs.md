---
title: "Stopping Syslog putting -- MARK-- into the logs"
date: 2007-07-13
forum: General Help
---

### Post by Rob_Quads on 2007-07-13
I have been trying to build a machine which spin down its discs. I have virtually got there with one of the only things stopping it being the fact that every 20 minutes the syslog prints MARK just to remind me its alive.

My machine is now stable enough I do not need this reminder any more so are happy to turn it off.

Normally this is done by editing the "/etc/init.d/sysklogd" file and where it states 

SYSLOGD="-u syslog"
replace with
SYSLOGD="-m 0 -u syslog"

I have done this but it appears that these parameters are not being passed to syslog when it is restarting. When I look at the ps listing of syslog it shows 

root      5113     1  0 Jul12 ?        00:00:00 /sbin/syslogd

I am sure it should show something along the lines of  

root      5113     1  0 Jul12 ?        00:00:00 /sbin/syslogd -u syslog

If I kill the syslog and start it myself supplying the -m parameters it works the way I want. I could hack the scripts but I would prefer to get it working properly

Anyone have any ideas as to why the parameters set in SYSLOGD are not being picked up?

---

### Post by dragon76 on 2007-09-05
I have used -m0 (without the space) and it worked for me IIRC

think it had to go in /etc/default/syslogd   though

---

### Post by mflint on 2007-09-10
> **dragon76 said:**
> think it had to go in /etc/default/syslogd   though

Excellent - just what I needed.

Looks like the comments at the top of "/etc/init.d/sysklogd" are misleading then... they should probably be replaced with a comment telling users to edit "/etc/default/syslogd" instead.

Matthew

---

