---
title: "[SOLVED] run a script through crontab every minute"
date: 2008-01-27
forum: General Help
---

### Post by motoperpetuo on 2008-01-27
i have a script that i would like the system to run once a minute, every minute. it definitely runs correctly from the command line, but i can't get it to run automatically through /etc/crontab to save my life. it's called gateway-fan and it's located in /usr/local/bin.

here are the contents of my /etc/crontab:
----------------------------------------------------------
# m h dom mon dow user command
17 * * * * root cd / && run-parts --report /etc/cron.hourly
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
* * * * * root /usr/local/bin/gateway-fan
#
---------------------------------------------------------
the last line is the one i added. i can't see how this is incorrect, but i guess it is because it certainly doesn't run. i'd greatly appreciate any help.

---

### Post by robert_pectol on 2008-01-27
> **motoperpetuo said:**
> i have a script that i would like the system to run once a minute, every minute. it definitely runs correctly from the command line, but i can't get it to run automatically through /etc/crontab to save my life. it's called gateway-fan and it's located in /usr/local/bin.

here are the contents of my /etc/crontab:
----------------------------------------------------------
# m h dom mon dow user command
17 * * * * root cd / && run-parts --report /etc/cron.hourly
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
* * * * * root /usr/local/bin/gateway-fan
#
---------------------------------------------------------
the last line is the one i added. i can't see how this is incorrect, but i guess it is because it certainly doesn't run. i'd greatly appreciate any help.

Try changing it to the following:
```

*/1 * * * * root /usr/local/bin/gateway-fan

```

---

### Post by heindsight on 2008-01-27
> **robert_pectol said:**
> Try changing it to the following:
```

*/1 * * * * root /usr/local/bin/gateway-fan

```

I don't see how that would make a difference. 

My guess is that the problem is either due to differences between bash and dash, or it's a path issue.

what happens when you run
```
sh /usr/local/bin/gateway-fan
``` in a terminal?

Check that all the commands (except built-in shell commands) used are available in one of the directories listed in the PATH definition in /etc/crontab

---

### Post by motoperpetuo on 2008-01-27
My guess is that the problem is either due to differences between bash and dash, or it's a path issue.

what happens when you run
```
sh /usr/local/bin/gateway-fan
``` in a terminal?

Check that all the commands (except built-in shell commands) used are available in one of the directories listed in the PATH definition in /etc/crontab[/QUOTE]

Here's my path statement from crontab:

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

my executable (gateway-fan) is located in /usr/local/bin and runs fine when i run it from a command line by simply navigating to that directory and typing 'gateway-fan'. when i type 'sh /usr/local/bin/gateway-fan' in a terminal i get:

/usr/local/bin/gateway-fan: 11: [[: not found
/usr/local/bin/gateway-fan: 17: [[: not found

i may have misunderstood your instructions. do i need the 'sh' at the beginning? it seems to run fine from any directory as long as i don't use the 'sh'. and of course, i still can't get it to run from crontab.

---

### Post by heindsight on 2008-01-27
> **motoperpetuo said:**
> 
my executable (gateway-fan) is located in /usr/local/bin and runs fine when i run it from a command line by simply navigating to that directory and typing 'gateway-fan'. when i type 'sh /usr/local/bin/gateway-fan' in a terminal i get:

/usr/local/bin/gateway-fan: 11: [[: not found
/usr/local/bin/gateway-fan: 17: [[: not found

i may have misunderstood your instructions. do i need the 'sh' at the beginning? it seems to run fine from any directory as long as i don't use the 'sh'. and of course, i still can't get it to run from crontab.

You'll notice a line like:
```
SHELL=/bin/sh
```
in /etc/crontab. this means that the commands in /etc/crontab are executed using the sh shell (in Ubuntu sh is dash) which is similar, but not identical to bash. when you run your script as
```
gateway-fan
```
then the script runs in your current shell (which is bash), but ```
sh gateway-fan
``` runs it using dash. Your problem is that dash doesn't understand some of the bash commands you used. Try putting 
```
#!/bin/bash
``` at the top of your script, that should sort out your problem.

---

### Post by motoperpetuo on 2008-01-27
awesome! that was it, i needed to add '#!/bin/bash' to the start of my script. i really, really appreciate the help.

---

