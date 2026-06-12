---
title: "Postfix/Dovecot/Squirrelmail &quot;Connection dropped by IMAP server&quot;"
date: 2014-12-10
forum: General Help
---

### Post by timothylegg on 2014-12-10
Hello all,

I'm no expert at e-mail systems, but I have been successful in the past at following howto documents and am trying it again.

I followed a wonderful and insightful document at:

[https://www.digitalocean.com/community/tutorials/how-to-configure-a-mail-server-using-postfix-dovecot-mysql-and-spamassasin](https://www.digitalocean.com/community/tutorials/how-to-configure-a-mail-server-using-postfix-dovecot-mysql-and-spamassasin)

with the following deviations:

/etc/dovecot/conf.d/10-master.conf

```
service imap-login {
  inet_listener imap {

   port = 143}

```

Because they instructed me to use port 0, which is not the correct port for IMAP (and the IMAPS didn't work with squirrelmail for some reason)

And so, with this, I can now telnet to port 143 (and squirrelmail no longer says the connection is refused).

When I log into squirrelmail successfully, I get an error "**ERROR: Connection dropped by IMAP server.**"

The servers all seem to work...  So I'm not sure what is going on.


> **root@example**:**/etc/dovecot/conf.d**# telnet example.com 143
Trying 127.0.1.1...
Connected to example.com.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS LOGINDISABLED] Dovecot (Ubuntu) ready.
^]


telnet> quit
Connection closed.
**root@example**:**/etc/dovecot/conf.d**# telnet example.com 993
Trying 127.0.1.1...
Connected to example.com.
Escape character is '^]'.
^]


telnet> quit
Connection closed.
**root@example**:**/etc/dovecot/conf.d**# telnet example.com 995
Trying 127.0.1.1...
Connected to example.com.
Escape character is '^]'.
^]


telnet> 



What are your thoughts?

---

