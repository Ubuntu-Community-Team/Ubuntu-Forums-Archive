---
title: "vsftpd wont log fail attempts"
date: 2008-04-21
forum: General Help
---

### Post by namik on 2008-04-21
I have vsftpd server running,the thing is: it logs successful attempts but not the fail attempts .
I need the fail attempts for blockhosts script.

here is the interesting part of my vsftpd.conf file


# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
#listen=YES


# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600



userlist_deny=NO
userlist_enable=YES
userlist_file=/etc//vsftpd.user_list

max_clients=3
max_per_ip=2
anon_max_rate=100000
#log_ftp_protocol= YES




thanks in advance

Regards Namik Delilovic

---

### Post by namik on 2008-04-22
ok i found the problem,if you have user lists enabled it wount log fail attempts.
Hope this will help someone in the future :)

Regards

---

