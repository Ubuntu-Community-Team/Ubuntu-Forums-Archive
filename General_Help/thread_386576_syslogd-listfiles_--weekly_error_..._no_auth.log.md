---
title: "syslogd-listfiles --weekly error ... no auth.log"
date: 2007-03-17
forum: General Help
---

### Post by rajko on 2007-03-17
I must be the only one with this problem on the planet. :( 
I created test conf file to simplify things:

syslog.conf_TEST (just 2 lines):
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog

[COLOR="Navy"]PART 1[/COLOR]

**syslogd-listfiles -f syslog.conf_TEST -a** outputs:
/var/log/syslog
/var/log/auth.log

**syslogd-listfiles -f syslog.conf_TEST**  outputs:
/var/log/syslog

**syslogd-listfiles -f syslog.conf_TEST --weekly**  outputs:
(nothing)

[COLOR="Navy"]PART 2[/COLOR]

I modified syslog.conf_TEST to:
auth,authpriv.*                 /var/log/auth.log_SOMETHING
*.*;auth,authpriv.none          -/var/log/syslog

and now **syslogd-listfiles -f syslog.conf_TEST --weekly**  outputs:
/var/log/auth.log_SOMETHING

If I change it back it wont work again... WTF???:confused: 
I'm completly confzed with this and can not figure this one out.:confused: 
Any suggestions are apriciated.:) 

Thanks in advance, Rajko.

---

### Post by rajko on 2007-03-17
Even stranger thing happened...
as I envestigated for possible bugs I tried few combinations
and it worked once and no more
it was strange only one .....
well i tried just now like crazy 50 times in a row and only once (2nd) time ...
pfff man ... this is crazy ...:confused: 
lets rock and roll I'm going for a 100 ..:guitar: 
:) :)

---

### Post by rajko on 2007-03-17
well no luck there 100 times did not produce even once...:( 
there must be ghost im my computer ...
I'm going for priest next ...

---

### Post by rajko on 2007-04-01
Well  after debuging I have found problem ...

in file /etc/cron.daily/sysklogd I added argument --ignore-size and now it looks like this:
for LOG in `syslogd-listfiles --ignore-size`

withouth --ignore-size cron will rotate log daily (not weekly) if file size is >1MB and I did not want that (which was default), because then I don't know which date is in which file and how much log time I have in logs.

Over and out :)
Rajko.

---

