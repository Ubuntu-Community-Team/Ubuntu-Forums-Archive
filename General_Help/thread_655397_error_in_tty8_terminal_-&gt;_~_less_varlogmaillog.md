---
title: "error in tty8 terminal -&gt; ~ less /var/log/maillog"
date: 2008-01-01
forum: General Help
---

### Post by Lightmans on 2008-01-01
Hello everybody and a happy new year!

Coludt somebody help me please, i got in my ubuntu 7.10 an error on 8th tty terminal in the startup phase. I think i got somewhere an error in my system and i dont know where i exactly have to search ...

Follwing problem or error:
If my PC with Ubuntu 7.10 and 2.6.22-14-generic kernel starts and boot,
and i switch in this time to the 8th tty terminal with (alt+f8 oder tty8) i see this ->

```

a lot of this char "~"
~
~
~
~
etc.
and at the bottom of the screen i got one line with this text:
-> less /var/log/mail.log (interrupt to abort)

i can do ctrl+c or ctrl+x but it comes again and reapeats.

```

i was searching and trying to find the error and i think i found the problem but i dont know where i can fix it.

i found this in my syslog:
```
Dec 30 16:13:53 debian 8-_-_var_-_log_-_mail.log: 8-_-_var_-_log_-_mail.log: terminating too quickly, waiting 10 seconds
Dec 30 16:14:03 debian 8-_-_var_-_log_-_mail.log: 8-_-_var_-_log_-_mail.log: client (pid 8269) killed by signal 2, respawning
Dec 30 16:15:26 debian ntpd[6144]: synchronized to 130.149.17.8, stratum 1
Dec 30 16:15:27 debian 8-_-_var_-_log_-_mail.log: 8-_-_var_-_log_-_mail.log: client (pid 8282) killed by signal 15, stopping 
```

and i also looked in to the running processes wth this command:

```
ps axf | grep mail
5728 Tty8 Ss+ 0:00 daemon --foreground -respawn    etc.... 
 
```

then i used the command  "kill 5728" and the terminal tty8 was free and the error was gone for a while.
but i know and if i try to restart, the error is back again...

can somebody help me pls and tell where i can fix that?

thx and greets,
Lightmans

---

### Post by Lightmans on 2008-01-01
Hello, nobody can help me with this problem?  :(

---

