---
title: "PostGrey Stopping Overnight!"
date: 2008-05-18
forum: General Help
---

### Post by kj6eo on 2008-05-18
Hello and thanks for reading my post.  I'm running Gusty with PostFix, PostGrey, and Spamassassin.  For some odd reason PostGrey just automatically quits working sometime overnight.  When I get up in the morning I see the following in /var/log/mail.log:

> May 18 03:58:50 ub postfix/smtpd[6449]: warning: connect to 127.0.0.1:60000: Connection refused
May 18 03:58:50 ub postfix/smtpd[6449]: warning: problem talking to server 127.0.0.1:60000: Connection refused

This warning is given because PostGrey isn't running.  To cure the problem I simply just start up PostGrey again.  However sometime during the next night it stops again by itself.

I did find an error listed in /var/log/mail.err (but I don't know if this has anything to do with the stopping problem:

> May 18 02:55:42 ub postgrey[4568]: fatal: Can't call method "txn_commit" on an undefined value at /usr/sbin/postgrey line 223.

Interestingly enough after reading the /var/log/mail.warn file, it does appear that the above error is killing postgrey:

> May 18 02:34:42 ub postfix/smtpd[6304]: warning: 124.218.128.117: hostname TC124-218-128-117.adsl.dynamic.apol.com.tw verification failed: No address associated with hostname
May 18 02:55:42 ub postgrey[4568]: fatal: Can't call method "txn_commit" on an undefined value at /usr/sbin/postgrey line 223.  
May 18 02:55:43 ub postfix/smtpd[6371]: warning: connect to 127.0.0.1:60000: Connection refused
May 18 02:55:43 ub postfix/smtpd[6371]: warning: problem talking to server 127.0.0.1:60000: Connection refused
May 18 02:57:28 ub postfix/smtpd[6375]: warning: connect to 127.0.0.1:60000: Connection refused
May 18 02:57:28 ub postfix/smtpd[6375]: warning: problem talking to server 127.0.0.1:60000: Connection refused
May 18 02:57:29 ub postfix/smtpd[6375]: warning: connect to 127.0.0.1:60000: Connection refused
May 18 02:57:29 ub postfix/smtpd[6375]: warning: problem talking to server 127.0.0.1:60000: Connection refused
May 18 02:57:41 ub postfix/smtpd[6375]: warning: connect to 127.0.0.1:60000: Connection refused
May 18 02:57:41 ub postfix/smtpd[6375]: warning: problem talking to server 127.0.0.1:60000: Connection refused
May 18 02:57:42 ub postfix/smtpd[6375]: warning: connect to 127.0.0.1:60000: Connection refused
May 18 02:57:42 ub postfix/smtpd[6375]: warning: problem talking to server 127.0.0.1:60000: Connection refused

I'm going to have a look at  /usr/sbin/postgrey (line 223) to see what it says there.  If any of you recognize this error any advice you might have would be greatly appreciated!

Regards,

Bill - KJ6EO

---

### Post by rduke15 on 2011-05-01
From the window that came up during my postgrey upgrade:

> Postgrey is now listening on port 10023 (rather than 60000), which brings its behavior closer to the default upstream settings.

You will need to adjust its configuration (usually in /etc/postfix/main.cf) accordingly.


Indeed, in /etc/postfix/main.cf, I had to replace 60000 with 10023 in this part:

> [FONT="Courier New"]smtpd_recipient_restrictions = permit_mynetworks,
  [...]
  check_policy_service inet:127.0.0.1:10023,[/FONT]


For the lazy and daring, just paste this in the shell:

```
perl -i.bak -pe 's/60000/10023/g' /etc/postfix/main.cf
```

---

