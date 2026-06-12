---
title: "Remote server monitoring software"
date: 2013-07-05
forum: General Help
---

### Post by aburgoyne on 2013-07-05
Hey, I'm just getting into the world of ubuntu server (installed as a home server on old laptop) but I'd like a way I can remotely check my server status' such as temperature and load remotely via a web page so I can check it wherever I am. I can't seem to find anything I can use, everything seems to be based at professional setups. Any help is appreciated thanks!

---

### Post by tgalati4 on 2013-07-05
nagios/cacti, ssh into a terminal and run a script that outputs those numbers.  If all you care about is uptime (and load) then *rwhod* and *rwho* is what you want.  That stands for Remote Who Daemon and it gives you the *ruptime* command which gives you remote uptime statistics.  Canonical has the Landscape monitoring product, but it may be overkill for a home/laptop server.

---

### Post by zitch on 2013-07-05
[Munin]("http://munin-monitoring.org/") can also provide this to you via a web page. In fact, you can have all your servers send its stats to a central server where you would log into and view your servers' stats in one place.  See the "munin" packages in the repositories and they can offer addons like temperature management and the like.

[Here's an example of what it looks like]("http://munin.ping.uio.no/") (UPDATE: And [here's]("http://munin.ping.uio.no/ping.uio.no/knuth.ping.uio.no/index.html#sensors")  a link to some example sensors graphs.)

---

### Post by aburgoyne on 2013-07-05
Just installed Nagios and it looks a bit of a mess! I want an easy way to spot the information I need but no idea where anything is on here! The landscape interface looks like something I'd want but as mentioned it does look a bit overboard for my needs. And you have to pay for it? I'd rather a pre-built approach than having to create a script to just push a couple of numbers my way too. Will have a look at Munin now cheers.

---

### Post by tgalati4 on 2013-07-05
You can also redirect syslog from the server to another machine.  This is helpful so that you can see the actual syslog entries on another, remote machine.  This method only really works if you have another machine (or server) that is running 24/7 to accept the syslog entries.

---

### Post by Habitual on 2013-07-05
zabbix should work "OOTB" for the "Zabbix server" which would be localhost/127.0.0.1. :)
Hope you can 'reach' that host from 'outside' your LAN(public IP)

---

### Post by marykaichini on 2013-07-10
I can share the tool that we are using to monitor the server. It is Anturis - the IT department says that it works great.

---

