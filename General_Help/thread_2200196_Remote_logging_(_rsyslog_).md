---
title: "Remote logging ( rsyslog )"
date: 2014-01-17
forum: General Help
---

### Post by mageta2 on 2014-01-17
I'm using ubuntu 12.04 64 bit server and I'm trying to get it to receive logs from a pfsense firewall. The firewall is already set up to send logs out on udp port 514, but I'm having problems setting up the server.

I edited /etc/rsyslog.conf to allow udp port 514, but I'm not familiar with the behavior of syslog, so I don't know what else I need to do.

1) Where will the logs be stored? They must be somewhere in /var/log but there are a lot of files in there and I'm not sure which one remote logs would go to.
2) Would permissions get in the way of the logs being received? What do I have to do to make sure that they aren't being shot down by a permission problem?
3) What about iptables? I've read conflicting things, first I read that iptables allows all connections by default, but some guides mention making exceptions, I've never touched iptables before, will it cause problems?

---

### Post by tgalati4 on 2014-01-18
The remote logs get dumped to /var/log/syslog on the host system with marked entries [remotemachinename]  Log Entry.  You can grep the remote machine name to pull out the logs.  It normally works without issue.  You might have to make a pinhole in your router firewall to let the remote syslog packets through.  You shouldn't need to configure IPtables unless you have previously created restrictive rules that block the rsyslog port.

---

### Post by mageta2 on 2014-01-18
> **tgalati4 said:**
> The remote logs get dumped to /var/log/syslog on the host system with marked entries [remotemachinename]  Log Entry.  You can grep the remote machine name to pull out the logs.  It normally works without issue.  You might have to make a pinhole in your router firewall to let the remote syslog packets through.  You shouldn't need to configure IPtables unless you have previously created restrictive rules that block the rsyslog port.

Hey, thanks for the reply. 

I just grepped that file and got a ton of hits on that hostname, so it's working.

---

