---
title: "What does this message mean?"
date: 2008-02-06
forum: General Help
---

### Post by cenwesi on 2008-02-06
I was looking through system log when i noticed these messages. Seems to happen every 5seconds.

/var/log/messages/
printk: 249 messages suppressed
rtc: lost some interrupts at 2048Hz

---

### Post by faulkes on 2008-02-06
**rtc?**

That sounds like the real time clock of the system.  Any additional messages in the logs?

Faulkes

---

### Post by cenwesi on 2008-02-06
It basically looks like this

Feb  6 10:37:02 ubuntusvr kernel: [4152808.515111] printk: 249 messages suppressed.
Feb  6 10:37:02 ubuntusvr kernel: [4152808.515118] rtc: lost some interrupts at 2048Hz.

---

### Post by EricBaenen on 2008-04-17
I'm getting this too on a 64 bit Ubuntu 7-10 install - are you running VMware Server?  

See this post at 
[http://communities.vmware.com/thread/116590?tstart=0](http://communities.vmware.com/thread/116590?tstart=0)

and in /etc/vmware/config try adding 
 host.useFastClock = FALSE

---

### Post by EricBaenen on 2008-04-17
Adding the line to /etc/vmware/config resolved my issue with these lines showing up in syslog

Eric

---

