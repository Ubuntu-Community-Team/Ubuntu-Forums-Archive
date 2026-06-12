---
title: "OS crashes/freezes randomly"
date: 2017-01-09
forum: General Help
---

### Post by jamesdean2 on 2017-01-09
[COLOR=#333333][FONT=sans-serif]Hello, this has been an issue for me for the last 8-9 months. Whenever it would crash, I would try to do the REISUB keys, but it would never work (because it crashed that badly), until this last crash (for some odd reason). I got the log file by typing this into terminal. t
[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]journalctl -b -1
[/FONT][/COLOR]


Unfortunately, I don't understand what the error is. If you could help me, I would be very grateful. Thanks for your help!!

edit: Apparently I cannot post the error log online, but here is a link to the crash log file (found in /var/crash).
[https://www.dropbox.com/s/dut7nstp96n0oq5/crash_info.txt?dl=0]("https://www.dropbox.com/s/hup3soocvnxafgr/crashboot.txt?dl=0")

---

### Post by chris354 on 2017-01-09
The log is dated november, is your computer time/date set correctly?

---

### Post by jamesdean2 on 2017-01-09
> **chris354 said:**
> The log is dated november, is your computer time/date set correctly?

I accidentally made a mistake. The file has been updated to the real issue. Please let me know if it doesn't seem like the REISUB was used in this log. I'm still very new to this stuff. haha. Thanks for your help!

---

### Post by chris354 on 2017-01-10
Okay that log isnt telling you what you need to know, It looks like its telling you that crash reporting is being set up. (Looks like the boot shutdown log).

Your reisub sequence will not log after u and only adds certain minimal entries into /var/log/syslog anyway.
See here for more information: [http://unix.stackexchange.com/questions/252711/where-is-altsysrqreuib-in-var-log-syslog](http://unix.stackexchange.com/questions/252711/where-is-altsysrqreuib-in-var-log-syslog)

Your crash logs are in /var/crash which should be more helpful in identifying the crash. 
See the accepted answer here with regards to tracing crashes: [http://askubuntu.com/questions/346953/how-to-read-and-use-crash-reports](http://askubuntu.com/questions/346953/how-to-read-and-use-crash-reports)

From this point its unlikely i will be able to help you further but i hope that with the correct logs somebody more experienced will be able to assist.

---

### Post by jamesdean2 on 2017-01-10
> **chris354 said:**
> Okay that log isnt telling you what you need to know, It looks like its telling you that crash reporting is being set up. (Looks like the boot shutdown log).

Your reisub sequence will not log after u and only adds certain minimal entries into /var/log/syslog anyway.
See here for more information: [http://unix.stackexchange.com/questions/252711/where-is-altsysrqreuib-in-var-log-syslog](http://unix.stackexchange.com/questions/252711/where-is-altsysrqreuib-in-var-log-syslog)

Your crash logs are in /var/crash which should be more helpful in identifying the crash. 
See the accepted answer here with regards to tracing crashes: [http://askubuntu.com/questions/346953/how-to-read-and-use-crash-reports](http://askubuntu.com/questions/346953/how-to-read-and-use-crash-reports)

From this point its unlikely i will be able to help you further but i hope that with the correct logs somebody more experienced will be able to assist.

I updated the post again with the crash log. haha. Thanks again!!

---

