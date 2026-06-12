---
title: "gdmflexiserver does not find custom servers"
date: 2007-12-07
forum: General Help
---

### Post by StijnVermeeren on 2007-12-07
Hi,

I am using an Acer laptop, and I'm trying to get the tutorial [HowtoSetupExternalMonitorForIntel915 on the Ubuntu Wiki]("https://wiki.ubuntu.com/HowtoSetupExternalMonitorForIntel915?highlight=%28CategoryHardware%29") to work.

The [servers] section in my /etc/gdm/gdm.conf-custom looks like this:
```

[servers]

[server-Standard]
name=Standard server (defined in gdm.conf-custom)
command=/usr/bin/X -br -audit 0 -layout DefaultLayout
flexible=true

[server-Separate]
name=Separate heads
command=/usr/bin/X -br -audit 0 -layout SeparateHeads
flexible=true

[server-Clone]
name=Clone heads
command=/usr/bin/X -br -audit 0 -layout CloneHeads
flexible=true
```

But when I run
```
gdmflexiserver -d
```
I do not get a menu asking me which server to choose, but the Standard server is automatically run.


```
gdmflexiserver -c "GET_SERVER_DETAILS Standard name"
```
gives "OK Standard server (defined in gdm.conf-custom)" as response, so the /etc/gdm/gdm.conf-custom is read by gdm. (Other definitions of [server-Standard] in for example /etc/gdm/gdm.conf have just "name=Standard server".)

But 
```
gdmflexiserver -c "GET_SERVER_DETAILS Clone name"
```
and
```
gdmflexiserver -c "GET_SERVER_DETAILS Separate name"
```
give both "ERROR 1 Server not found".

```
gdmflexiserver -c "GET_SERVER_LIST"
```
gives just "OK Standard".

So only the [server-Standard] is read in gdm.conf-custom. Does anyone know why?

---

### Post by motin on 2008-02-24
Same for me. Have you filed a bug report about it?

EDIT: Filed one: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/195296](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/195296)

Is this the same problem - then please confirm it. 

Cheers!

---

