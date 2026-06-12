---
title: "Trouble Sending Mail Via Telnet"
date: 2018-08-28
forum: General Help
---

### Post by pkjm17 on 2018-08-28
Am trying to send a test email to my gmail account. I am able to telnet to localhost 25. Everything seems to go ok, but the email never gets sent. This is the output from /var/log/mail.log

```
Aug 28 21:32:31 2fast2furious postfix/smtpd[3214]: connect from localhost[127.0.0.1]
Aug 28 21:33:22 2fast2furious postfix/smtpd[3214]: 3793FA102C: client=localhost[127.0.0.1]
Aug 28 21:33:39 2fast2furious postfix/cleanup[3218]: 3793FA102C: message-id=<20180829013322.3793FA102C@2fast2furious.fios-router.home>
Aug 28 21:33:39 2fast2furious postfix/qmgr[3210]: 3793FA102C: from=<user1@example.com>, size=358, nrcpt=1 (queue active)
Aug 28 21:33:41 2fast2furious postfix/smtpd[3214]: disconnect from localhost[127.0.0.1] helo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Aug 28 21:34:09 2fast2furious postfix/smtp[3219]: connect to gmail-smtp-in.l.google.com[172.217.197.27]:25: Connection timed out
Aug 28 21:34:09 2fast2furious postfix/smtp[3219]: connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c0f::1b]:25: Network is unreachable
Aug 28 21:34:39 2fast2furious postfix/smtp[3219]: connect to alt1.gmail-smtp-in.l.google.com[64.233.186.26]:25: Connection timed out
Aug 28 21:34:39 2fast2furious postfix/smtp[3219]: connect to alt1.gmail-smtp-in.l.google.com[2800:3f0:4003:c00::1b]:25: Network is unreachable
Aug 28 21:35:09 2fast2furious postfix/smtp[3219]: connect to alt2.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection timed out
Aug 28 21:35:09 2fast2furious postfix/smtp[3219]: 3793FA102C: to=<myemailaddress@gmail.com>, relay=none, delay=121, delays=31/0.01/90/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection timed out)
```

This is what I did:
```
pat@2fast2furious:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 2fast2furious.fios-router.home ESMTP Postfix (Ubuntu)
HELO localhost
250 2fast2furious.fios-router.home
MAIL FROM: user1@example.com
250 2.1.0 Ok
RCPT TO: myemailaddress@gmail.com
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
This is a test email.

.
250 2.0.0 Ok: queued as 3793FA102C
quit
221 2.0.0 Bye
Connection closed by foreign host.
```

Attached is what I have in  /etc/postfix/main.cf. Am I missing or do I need to change anything in it?

---

### Post by SeijiSensei on 2018-08-29
Your provider probably blocks outbound SMTP connections as an anti-spam measure. Your system is blocked from sending the mail to gmail.

---

