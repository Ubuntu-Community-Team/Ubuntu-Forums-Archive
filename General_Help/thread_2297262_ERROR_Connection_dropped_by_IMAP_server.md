---
title: "ERROR: Connection dropped by IMAP server"
date: 2015-10-02
forum: General Help
---

### Post by Utkarsh_Raval on 2015-10-02
I configure the squirrelmail webmail server in AWS amazon ubuntu 14.04


Whenever I am trying to login with my username and password, it will display error like:


**ERROR: Connection dropped by IMAP server**


Is there any one who able to resolve this issue ??

---

### Post by SeijiSensei on 2015-10-02
Where is the IMAP server located?  On the same machine as Squirrelmail?  If so, are you connecting to it via "localhost"?

---

### Post by Utkarsh_Raval on 2015-10-03
Yes,

How can I connect it via "localhost" ??

---

### Post by SeijiSensei on 2015-10-03
Did you run the config.pl script to set up Squirrelmail?  What server did you specify?  You should have "localhost" (or 127.0.0.1) for the SMTP and IMAP servers, and ports 25 and 143 respectively.  I presume you're using dovecot for IMAP services?  What authentication methods does it support?

What do you see in /var/log/mail.log when the connection is dropped?  

If you run the command
```
telnet localhost 143
```
does it reply with a banner like this?
```
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot ready.
```
If you allow plain-text logins, you can test by typing the command
```
1 login username password
```
after the banner displays.

Dovecot can be fairly complex to set up.  Have you read [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)?

---

### Post by rrbarton on 2015-12-11
The 2.2.9 version of dovecot that's the latest with Ubuntu 14.04.3 has a bug with shared mailboxes that causes a segmentation fault.  2.2.13 is said to have a fix.  I wonder when Ubuntu will include the latest version of dovecot with that fix.  Perhaps, your configuration has a shared mailbox that's hitting this problem.

---

### Post by SeijiSensei on 2015-12-11
That's useful information, but did you notice that this person has never replied to my suggestions made two months ago?  Either he fixed the problem or gave up.

As you might tell from my signature, I find people like the OP really annoying.  I probably spent ten or fifteen minutes writing a detailed response and never got any reply.  That happens all the time here and represents a fundamental lack of respect for those of us trying to help.

---

