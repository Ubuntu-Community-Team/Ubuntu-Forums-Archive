---
title: "syslog-ng starts every day"
date: 2017-12-06
forum: General Help
---

### Post by backspin on 2017-12-06
I have a couple of Ubuntu servers running 14.04.1-Ubuntu. One of these servers is a primary and another is failover, so I keep certain services disabled on failover unless the primary goes down. One of the services I need to keep disabled is syslog-ng. Even though I've run the commands to kill the syslog-ng process and run the command "update-rc.d syslog-ng disable", syslog-ng starts itself back up every day. 

There is documentation to disable a service by "removing" it by doing the following....  "update-rc.d -f syslog-ng remove"    However, I don't know what's involved in re-enabling the service once it is removed in this fashion.

Ideas?

---

### Post by fekete77-robert on 2017-12-07
Hi, probably logrotate runs every night, and restarts the logging daemon.

---

### Post by fekete77-robert on 2017-12-07
Another possibility is that i[COLOR=#222222][FONT=arial]t starts back up due to syslog.socket being[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]socket-activated. Disable syslog.socket, and syslog-ng will stop[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]starting back up too.[/FONT][/COLOR]

---

### Post by backspin on 2017-12-07
> **fekete77-robert said:**
> Another possibility is that i[COLOR=#222222][FONT=arial]t starts back up due to syslog.socket being[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]socket-activated. Disable syslog.socket, and syslog-ng will stop[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]starting back up too.[/FONT][/COLOR]

How would I go about disabling the syslog socket?

---

