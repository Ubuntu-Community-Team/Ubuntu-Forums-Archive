---
title: "How to redirect /var/log/wtmp to a linux log server"
date: 2013-02-21
forum: General Help
---

### Post by tlparolin on 2013-02-21
Hi all...
I need to obtain logs for all logins in ubuntu computers in my environment.
I have one log server that can retrieve the /var/log/auth.log, but i need information like "last" command:

user  pts/0        host Fri Feb  8 14:24 - 17:01  (02:37)

How can i do this? There are some way to retrieve the /var/log/wtmp from my linux clients? How to redirect wtmp from clients to my log server?

Thanks

---

### Post by albandy on 2013-02-21
> **tlparolin said:**
> Hi all...
I need to obtain logs for all logins in ubuntu computers in my environment.
I have one log server that can retrieve the /var/log/auth.log, but i need information like "last" command:

user  pts/0        host Fri Feb  8 14:24 - 17:01  (02:37)

How can i do this? There are some way to retrieve the /var/log/wtmp from my linux clients? How to redirect wtmp from clients to my log server?

Thanks

Make the authentication happen in the server, for example with NIS.

---

### Post by tlparolin on 2013-02-21
All logins is validated with ldap.
But in ldap's log, doesn't retrieve the information that i need (like last command)
Windows logins, using ldap/samba appears in last command on the server, so i think that redirecting wtmp from linux clients would be usefull to know users logins..
thanks

---

### Post by schragge on 2013-02-21
With *last -f [color=green]file[/color]* you can specify which file *last* should use instead of */var/log/wtmp*. So, retrieve */var/log/wtmp* like you do with */var/log/auth.log*, then *last -f* retrieved file.

---

### Post by tlparolin on 2013-02-21
Thank for all reply...
This is a great community!!! 
Well.. i send my /var/log/auth.log with rsyslog:

auth,autpriv.* @logserver

How can i send wtmp?
I don't know how can i send through rsyslog

---

### Post by schragge on 2013-02-21
Sorry, I didn't think about it. AIUI, you cannot redirect *wtmp* through rsyslogd. :( Would a cron job that periodically sends the output of *last* to the remote server fit your purpose? Also, some LDAP-based directory services like [OpenDJ](http://opendj.forgerock.org/doc/admin-guide/index/chap-ldap-operations.html#extensible-match-search) let you define password policy that logs last login time for each user, but I guess it's beyond the abilities of a vanilla LDAP server.

---

### Post by tlparolin on 2013-02-21
Thanks again..Now i solved my problem...
I did like you said: an script to call last command putting out to /var/log/auth.log

My steps:

1 - schedule to /etc/cron.daily/users:
    #!/bin/bash
    sudo last >> /var/log/auth.log

2 - make executable: chmod +x /etc/cron.daily/users

3 - changed wtmp in /etc/logrotate.conf to daily and rotate 90 days

Now, i get the auth.log in server with output from "last"
from now on, i can do some kind of filter to clean auth.log in server to get only last output...

This is more or less what i did to get working.
Thanks

---

