---
title: "How can I find out what's historically caused high CPU and crashes?"
date: 2020-03-01
forum: General Help
---

### Post by cable_guy on 2020-03-01
Morning,

I'm trying to work out what's causing my Ubuntu 16.04 server to 1) Spike it's CPU and 2) crash

I mainly use this machine for serving files in my home network.  

I remember starting this off a couple of weeks ago I ran a command to enable some sort of logging, in the hope I could query these but i've run a blank trying to find what I enabled to reignite my search.

thanks in advance

---

### Post by linuxyogi on 2020-03-01
Use the ```
top
``` command.

---

### Post by cable_guy on 2020-03-01
thanks I do use top for the instant/real time analysis but what i'm trying to do is figure out what has historically caused the crashes when the system is unresponsive.

---

### Post by dragonfly41 on 2020-03-01
Just some ideas since I rarely experience freezing.

(a) I installed stacer for Ubuntu monitoring.

(b) For analysing a history of dated log files you can try using [petit]("http://crunchtools.com/software/petit/") which analyses patterns in log files.

(c) And lynis is a useful auditing tool.


When I last had freezing in an older setup it was related to too many open tabs in browser.

---

### Post by TheFu on 2020-03-01
```
$ jounalctl -p err
```

This assumes you've told systemd/journald to keep logs between boots.

But I'm a big believer in using a performance monitoring tool on servers. Something like munin or cacti or nagios. Those are usually too hard for typical end-users to configure.  Perhaps [https://www.monitorix.org/](https://www.monitorix.org/) is easier?

---

