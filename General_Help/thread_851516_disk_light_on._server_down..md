---
title: "disk light on. server down."
date: 2008-07-06
forum: General Help
---

### Post by cnschulz on 2008-07-06
Hi, 

I have an interesting problem.

I am running hardy headless and do regular (bi-weekly) update/upgrades. last week i did a dist-upgrade because i could see that the kernel packages were being held back.

Since then I have the server go down (completely) three times. The disk light is permanently on and no serveices respond (including local command line).

Im not sure where to start. The only thing interesting in the logs is that mysqlcheck has found some "corrupt" databases. However when i run mysqlcheck manually they all report as OK (Im assuming in this case "corrupt" means "currently open")

So... I understand there are a lot of parameters here... I have a lot of software on this server. But to have it completely shutdown is pretty serious.

Any advice on where to start looking is appreciated.

Cheers

c.

---

### Post by ModelM on 2008-07-06
If you don't usually keep a keyboard plugged into this machine, try running it with one installed. The next time it hangs, flashing keyboard LEDs indicate a kernel panic. If the LEDs aren't flashing, it's probably something else.

I realize this isn't much, but it's a start...

---

### Post by cnschulz on 2008-07-06
thanks, 

keyboard is in... no lights.

maybe its time i fscked myself?

c.

---

### Post by lisati on 2008-07-06
> **cnschulz said:**
> maybe its time i fscked myself?:lolflag: The non-tach-savvy lady of the house appreciated this!

I'm unable to come up with anything more useful at this stage than "Keep on smiling!!"

Good luck.

---

### Post by cnschulz on 2008-07-06
im getting closer:

i believe it is apparmor casing the problems...

bind9 and mysql are having serious permissions issues and if they dont work... bad things happen to a server.

/etc/apparmor.d/force-complain/usr.sbin.named
/etc/apparmor.d/force-complain/usr.sbin.mysqld

appear in the boot messages

and this appears in syslog

Jul  7 02:35:10 zoidberg kernel: [24919.914764] audit(1215362110.197:110): type=1502 operation="inode_rename" requested_mask="rw::" denied_mask="rw::" name="/var/lib/named/var/log/bind9/query.log.0" pid=4501 profile="/usr/sbin/named" namespace="default"

so... im assuming apparmor is not allowing mysql and bind9 (named) to have the permissions they want.

im finding bits and peices of information around but if anyone has experience here, please let me know.

---

### Post by cnschulz on 2008-09-02
yep. its apparmor.

the latest update to ubuntu broke it again because apparmor is now "builtin" (ive managed to disable it...again) 

This machine has been upgraded constantly since 7.04. Ive heard of apparmor problems with mysql and others but this seems to be causing *hardware* failures...

any ideas where to start?

:-0

---

