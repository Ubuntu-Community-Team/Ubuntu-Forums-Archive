---
title: "Postfix stopped logging to /var/log/mail.*"
date: 2018-09-04
forum: General Help
---

### Post by julba on 2018-09-04
I am running Ubuntu 16:04 on 3 machines. On two of them, for some unknown reason postfix stopped logging to /var/log/mail.* a long time ago (2018-01-07) while on the 3rd machine the log files (e.g. /var/log/mail.log) are filled normally. I did not bother about that problem before, but  now I need to have the logging working on all 3 machines. 

I have spent several days to try to find out what is wrong but I could not find the reason. I searched the Internet for similar problems and found that many users have had that problem. There were a lot of good suggestions for what could be wrong and how to solve it. I tried all them, but I cannot get the mail log files to be filled on the two machines.

 All the rsyslog files, including permissions etc, are identical on the 3 systems. I re-installed (apt install --reinstall) rsyslog but it did not help. The postfix configuration files are slightly different on the 3 machines, but I don't think those differences have anything to do with the missing log files.

Is there a way to run rsyslogd and/or postfix in debugging mode to get some messages from those two facilities that may indicate what is wrong? Any advice for how to solve this problem are highly appreciated.

Johan

---

