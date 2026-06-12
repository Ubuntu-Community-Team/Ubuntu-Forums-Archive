---
title: "Ubuntu 8.04 hangs"
date: 2008-06-18
forum: General Help
---

### Post by crabhunt on 2008-06-18
I recently updated the kernel version to 2.6.24-18-generic and since then every now and then the system hangs, its really painful as all the debugging session of my work worth hours get lost this way...

Please help and let me know if I can furnish any more information to solve this issue.

thanks

---

### Post by cmnorton on 2008-06-18
Examining the output of

dmesg
tail /var/log/messages
tail /var/log/syslog
tail /var/log/kern.log

might tell you something. 

Also, what are you doing at the time of the hang?

Is it possible for you to write a shell script to output ps to a file, so you can examine after rebooting?

What kind of hardware is this?

---

### Post by crabhunt on 2008-06-18
> **cmnorton said:**
> Examining the output of

dmesg
tail /var/log/messages
tail /var/log/syslog
tail /var/log/kern.log

might tell you something. 

Also, what are you doing at the time of the hang?

Is it possible for you to write a shell script to output ps to a file, so you can examine after rebooting?

What kind of hardware is this?


I have attached the logs you asked for. The script you asked for, how can I make sure that it dumps the output of ps just before the system hangs unless I dump it very often ?

The hardware is a IBM Thinkpad T60 running 32 bit x86.

The system hanged the last time while I was just runnning 3 ssh sessions to a remote machine, playing some music and opera browser was running as well, but it hangs even without these particular applications running e.g. last time it hanged was while it was doing nothing other than downloading a torrent....

---

### Post by irshadcharm on 2008-06-18
did u try going into the failsafe gnome session and remove any unwanted package that might cause the problem....?

---

