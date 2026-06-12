---
title: "Logcheck ignoring ignore files?"
date: 2007-02-16
forum: General Help
---

### Post by PgR on 2007-02-16
I'm trying to configure logcheck to ignore some syslog entries on 6.10. For instance postfix reporting "NOQUEUE" when refusing to relay.

I've tried writing regexp's in /etc/logcheck/ignore.d.server/postfix to do this (reportlevel="server") but not had any joy. I've even chosen predictable entries, written a regexp for exactly those ones, and it *still* doesn't ignore them.

I'm hoping that for some reason it isn't reading the file correctly, rather than my regexp being duff. How can I verify that logcheck is parsing the correct files? If I run with -D then it lists all the files in all the ignore.d.xxx directories, not just the dir it's meant to be parsing.

---

### Post by PgR on 2007-02-20
I've tried removing /etc/logcheck/ignore.d.server/postfix, and logcheck generates huge emails, so it's definitely parsing the file OK.

Any bright ideas? A typical entry in syslog is

Feb 20 21:30:28 mybox postfix/smtpd[14467]: NOQUEUE: reject: RCPT from otherbox.other.domain.name[192.168.10.1]: 504 5.5.2 <otherbox>: Helo command rejected: need fully-qualified hostname; from=<user@mydomain.name> to=<user@mydomain.name> proto=SMTP helo=<otherbox>

and the regex I've tried to exlude them with is

^\w{3} [ :0-9]{11} mybox postfix/smtpd?\[[0-9]+\]: NOQUEUE: reject: RCPT from otherbox\.other\.domain\.name\[192\.168\.10\.1\]: 504 5\.5\.2 <otherbox>: Helo command rejected: need fully\-qualified hostname; from=<user@mydomain\.name> to=<user@mydomain\.name> proto=SMTP helo=<otherbox>$

But still they get through... What is up with my lovely regex?

---

### Post by Mr. C. on 2007-02-22
You've fallen into a perl trap.

<user\@mydomain\.name> to=<user\@mydomain\.name>

You need to escape your @ signs, as they are being parsed and interpolated as @mydomain, the array.

Also, you can change [0-9] into \d .

Try my new logwatch postfix filter if you want to see what your postfix is doing:

[http://www.mikecappella.com/logwatch/postfix.tgz](http://www.mikecappella.com/logwatch/postfix.tgz)

Its also in the most recent logwatch release.

MrC

---

### Post by PgR on 2007-02-23
Thanks for that, Mr.C

I've also found that as NOQUEUE is in the "security events" section of logcheck, the regex needs to be in /etc/logcheck/violations.ignore.d/postfix not ../ignore.d.server/postfix else it ignores it entirely.

Some day I'll understand all this.

---

