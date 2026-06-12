---
title: "telnet problem"
date: 2008-02-12
forum: General Help
---

### Post by Black Mage on 2008-02-12
When I try to telnet into my computer for testing my postfix mail server, I came across this problem. Anything I type is not read. It goes like this:

```

telnet localhost 25
Trying 127.0.0.1.....
Connected to localhost.localdomain.
Escape character is ']'.
ehlo localhost
quit

```

But no matter what I type, nothing is never read. Any ideas why and am I just being a noob?

---

### Post by Jussi Kukkonen on 2008-02-13
I'm guessing postfix config problem.Do *tail -f /var/log/mail.log* (or wherever you logs go) before you try telnetting.

---

### Post by Black Mage on 2008-02-13
Ok, my /var/log/mail.log looks like this:

```

Feb 13 04:56:17 mainserver postfix/smtpd[10324]: fatal: bad boolean configuration: smtpd_delay_reject = yes d
Feb 13 04:56:18 mainserver postfix/master[8282]: warning: process /usr/lib/postfix/smtpd pid 10324 exit status 1
Feb 13 04:56:18 mainserver postfix/master[8282]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Feb 13 04:57:18 mainserver postfix/smtpd[10326]: fatal: bad boolean configuration: smtpd_delay_reject = yes d
Feb 13 04:57:19 mainserver postfix/master[8282]: warning: process /usr/lib/postfix/smtpd pid 10326 exit status 1
Feb 13 04:57:19 mainserver postfix/master[8282]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Feb 13 04:58:19 mainserver postfix/smtpd[10329]: fatal: bad boolean configuration: smtpd_delay_reject = yes d

```

So what does that mean?

---

### Post by Black Mage on 2008-02-13
Ok, I fixed that one on my own.
Not there is this one:

```

Feb 13 08:20:01 mainserver postfix/smtp[11341]: fatal: parameter smtp_helo_timeout: bad time value or unit: 60s # how many address can be used $
Feb 13 08:20:02 mainserver postfix/master[11297]: warning: process /usr/lib/postfix/smtp pid 11341 exit status 1
Feb 13 08:20:02 mainserver postfix/master[11297]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling
Feb 13 08:20:14 mainserver postfix/smtpd[11326]: disconnect from localhost.localdomain[127.0.0.1]
Feb 13 08:21:02 mainserver postfix/smtp[11343]: fatal: parameter smtp_helo_timeout: bad time value or unit: 60s # how many address can be used $
Feb 13 08:21:03 mainserver postfix/master[11297]: warning: process /usr/lib/postfix/smtp pid 11343 exit status 1
Feb 13 08:21:03 mainserver postfix/master[11297]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling


```

---

