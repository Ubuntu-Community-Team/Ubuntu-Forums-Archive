---
title: "Check_MK - Livestatus not loading in Nagios"
date: 2015-02-19
forum: General Help
---

### Post by david.bell on 2015-02-19
So, I have installed Nagios 4 (its working just fine) and I'm looking at setting up Thunk. So before that, i'm working on getting Livestatus working. I went through the install (just did the full check_mk install) and it seems to be working. I can run cmk command line queries. But when I load nagios and try to use Thunk's back end configuration I get messages about the connection being refused.

In my nagios.cfg I have added:```
event_broker_options=-1
broker_module=/usr/lib/check_mk/livestatus.o /usr/local/nagios/var/rw/live

```
/usr/local/nagios/var/rw/live was created after restarting nagios, so that seems to be working.

Here are my livestatus errors in Nagios (I left out everything before the livestatus notifications): [http://pastebin.com/j3jAiXPc](http://pastebin.com/j3jAiXPc)

---

