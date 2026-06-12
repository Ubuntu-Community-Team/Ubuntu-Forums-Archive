---
title: "reason for rebooting"
date: 2007-06-03
forum: General Help
---

### Post by auditory on 2007-06-03
i am using ubuntu 7.04 and it is working fine.

last week, i left the machine on with some simulations working on.

but this morning, i found out, the computer was rebooted.

it is working without any problem. but i want to know

why and when the machine was rebooted.

Which logs or files should i look into?

---

### Post by fanatik on 2007-06-04
it was probably a power cut! have a look in /var/log and see if anything is mentioned in messages or syslog, or any other logs files.

---

### Post by Shazaam on 2007-06-04
Do you have auto-update enabled? Some updates need a reboot.

---

### Post by eentonig on 2007-06-04
> **Shazaam said:**
> Do you have auto-update enabled? Some updates need a reboot.

But even with auto-update I wouldn't expect to see an automatic reboot. Not?

---

### Post by Crafty Kisses on 2007-06-04
> **eentonig said:**
> But even with auto-update I wouldn't expect to see an automatic reboot. Not?

It's possible, but I don't see that being the issue in this case.

---

### Post by pak33m on 2007-06-04
auditory,

var/log is the location where you should find all Linux log files.  You should start with the messages log file which is the system log file.
 
To view a listing of what log files have been generated use the following command:

ls &#8211;l /var/log

To view the contents of the common log file (or the system log file) use any one of the following commands:

tail -f /var/log/messages (Monitor live activity in the log)
less /var/log/messages (View parts using the space bar or enter key)
more -f /var/log/messages (View parts using the space bar or enter key)
vi /var/log/messages (Enter the file in editor mode) 

This is a sample of the output: 

Jul 17 22:04:25 router  dnsprobe[276]: dns query failed
Jul 17 22:04:29 router last message repeated 2 times
Jul 17 22:04:29 router  dnsprobe[276]: Primary DNS server Is Down... Switching To Secondary DNS server
Jul 17 22:05:08 router  dnsprobe[276]: Switching Back To Primary DNS server
Jul 17 22:26:11 debian -- MARK --
Jul 17 22:46:11 debian -- MARK --
Jul 17 22:47:36 router  -- MARK --
Jul 17 22:47:36 router  dnsprobe[276]: dns query failed
Jul 17 22:47:38  debian kernel: rtc: lost some interrupts at 1024Hz.
Jun 17 22:47:39  debian kernel: IN=eth0 OUT= MAC=00:0f:ea:91:04:07:00:08:5c:00:00:01:08:00 SRC=61.4.218.24 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=21599 DF PROTO=TCP SPT=59297 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0

Common log files names:

/var/log/message (General message and system related stuff
/var/log/auth.log (Authentication logs
/var/log/kern.log (Kernel logs)
/var/log/cron.log (Crond logs)
/var/log/maillog (Mail logs)
/var/log/qmail/ (Qmail log directory (more files inside this directory)
/var/log/httpd/ (Apache access and error logs directory)
/var/log/lighttpd (Lighttpd access and error logs directory)
/var/log/boot.log (System boot log)
/var/log/mysqld.log (MySQL database server log file)
/var/log/secure (Authentication log)
/var/log/utmp or /var/log/wtmp (Login records file)

Hope this helps in your endeavors.

---

### Post by auditory on 2007-06-04
Thanks for many replies.
I could see when the machine rebooted, but not why.
I couldn't find any improper messages or failure.

It might be power-cut, but not sure.
If it was power-cut i think the machine left turned off.

It might be  due to the auto-update. 
I'd better disable auto-update.

Thank you for great infos.

---

