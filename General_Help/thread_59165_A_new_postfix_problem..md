---
title: "A new postfix problem."
date: 2005-08-23
forum: General Help
---

### Post by musther on 2005-08-23
I've fixed my config, so now postfix seems to work, it accepts mail on SMTP, but the mail doesn't go anywhere, the log has quite a few lines that say.

Warning: connect to transport smtp: Connection refused

And whenever a message is received it says it's been defered because 'transport unavailable' as you can see from above.

I can't figure out why this is, the port is not firewalled, or blocked by my ISP, I can connect to machines on 25 and machines on the net can see my SMTP server on 25.

Any ideas?

---

### Post by ape on 2005-08-23
Are there any other errors in the mail.info  file when you start postfix up?  What does the contents of your /etc/postfix/master.cf look like relating to the smtp service?

---

### Post by musther on 2005-08-23
The full line in mail.log is:

postfix/oqmgr[8237]: warning: connect to transport smtp: Connection refused

The same warning is in mail.info.

when it tries to send a message, it produces:

```
postfix/oqmgr[8140]: ECE542C769: to=<jmusther@hotmail.com>, relay=none, delay=11464, status=deferred (delivery temporarily suspended: transport is unavailable)
```

My master.cf looks like this:

```
smtp      inet  n       -       -       -       -       smtpd
smtps     inet  n       -       -       -       -       smtpd
submission inet n       -       -       -       -       smtpd  -o smtpd_etrn_restrictions=reject
628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       -       300     1       qmgr
qmgr      fifo  n       -       -       300     1       oqmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  n       -       n       -       -       smtp
relay     unix  n       -       -       -       -       smtp   -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil

```

---

### Post by ape on 2005-08-24
Do you have any filters set up or are you attempting to use SpamAssassin or Amavis?  Do you have a content_filter line in your main.cf?

---

### Post by musther on 2005-08-24
[QUOTE=ape]Do you have any filters set up or are you attempting to use SpamAssassin or Amavis?  Do you have a content_filter line in your main.cf?[/QUOTE]

No filters, no SpamAssassin, no Amavis, no content_filter line.  I wan't to get the basic config working before I try to get filters or SpamAssassin working.

---

