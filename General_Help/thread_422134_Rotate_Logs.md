---
title: "Rotate Logs"
date: 2007-04-24
forum: General Help
---

### Post by bananabob on 2007-04-24
Currently I have a log created by getmail in my $HOME directory. 

Is it possible to place this in /var/log and have the log rotated by the system?

---

### Post by asipi on 2007-04-26
maybe that is user specific log that's why in your $HOME... you have to set in getmail I guess where it should put it's logfile, then read logrotate's manpage (man logrotate) it is not difficult to create a new rule for rotating another log ;) check the files in /etc/logrotate.d and based on them create your own

---

### Post by bananabob on 2007-04-26
Yes it is a user created log file. Can you use logrotate with Ubuntu I read somewhere that it uses syslog (I think that was what it was called) rather than logrotate. Wouldn't having both running confuse things?

---

### Post by asipi on 2007-04-26
try to set getmail to log directly into /var/lo and then configure logrotate
syslog facility could work if the program can log into syslog's socket because it sorts the incoming messages based on identifiers, and anyway more complicated

---

### Post by bananabob on 2007-04-29
I tried to get this going ny using /var/log/ but ran into permission problems. My userid is not allowed to create logs in /var/log 

Not a problem I thought. I can edit the logrotate parameters for the getmail log so that it rotates in my own home directory. And what do you know? It works!

Thanks for your help

---

