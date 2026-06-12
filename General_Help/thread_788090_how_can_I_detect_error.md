---
title: "how can I detect error?"
date: 2008-05-09
forum: General Help
---

### Post by obocho on 2008-05-09
hi guys,

Is there any code, method, [whatever] to detect errors?
I mean something like "sudo chechmyerror" :confused:

so that I can find problems and maybe correct them. 

thanks in advance...

---

### Post by ilrudie on 2008-05-09
Can you give more details on what you are trying to do?  Are you looking for?  Compile errors, hard disk errors, network errors, memory management errors, etc...?  Are you trying to look up error codes?

---

### Post by obocho on 2008-05-09
fair question : ) 

actually I meant "system errors". 
any unstable, corrupt or somehow not properly working system issues which may cause future problems [even though now my system works w/o any problem].

and if this does not make any sense, maybe I don't know what to look for.  
Which errors are traceable and how can I detect "any possible problem" in advance. 

thx again

---

### Post by ilrudie on 2008-05-09
Linux uses the syslogd daemon to log messages.  It is configured in /etc/syslog.conf.  Various logs already exist and you can always check those logs for errors but you can also make a new log by editing the syslog.conf file.  to do so ```
sudo cp /etc/syslog.conf /etc/syslog.conf.bak
``` to make a backup syslog configuration.  Then edit the syslog,conf with something like ```
sudo vi /etc/syslog.conf
```  Add a line at the bottom such as
```
*.err<tab>/var/log/err.log
``` where <tab> is one or more tabs.  Then you should run 'touch /var/log/err.log' to make sure that file exists.  You can then restart the syslogd daemon by running ```
sudo /etc/init.d/sysklogd restart
``` causing it to reread your conf file.  Finally you can test that your new improved logging is working by running ```
logger -p kern.err "test kern.err"
```  Now go check your newly created log for the message.  That should be a good start.

---

