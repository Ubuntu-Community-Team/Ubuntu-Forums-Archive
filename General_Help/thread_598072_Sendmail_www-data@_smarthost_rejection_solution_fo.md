---
title: "Sendmail www-data@ smarthost rejection solution found"
date: 2007-10-31
forum: General Help
---

### Post by jamesT0723 on 2007-10-31
[FIX] FROM:www-data@localhost,Sendmail,smarthost block, PHP


Sendmail can be configured in a way to change the FROM:www-data@localhost.In my case this is what was causing the messages to be rejected by a "Smart Host".


After installing sendmail with apt-get
edit the php.ini file and ensure that;
sendmail_path =/usr/sbin/sendmail -t -i

My first success was using the -f option.
sendmail_path =/usr/sbin/sendmail -t -i [email]-fmailer@yourdomain.com[/email]
This allowed messages to delivered, but viewing the "full header" of the received message revealed an "X-Authentication-Warning:"

There is a better way. Check this out:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers)
Especially the section titled; Using Sendmail to Change the Sender's Email Address

---

### Post by sarble on 2008-01-23
Thanks :) This is exactly what I needed...

---

### Post by eluzi on 2008-04-15
I'm still having trouble with it... 


Tried this:
> My first success was using the -f option.
sendmail_path =/usr/sbin/sendmail -t -i [email]-fmailer@yourdomain.com[/email] 


and this...

> 
There is a better way. Check this out:
[http://www.linuxhomenetworking.com/w...x_Mail_Servers](http://www.linuxhomenetworking.com/w...x_Mail_Servers)


... and nothing worked...

The company has its mail server, and I've got a server with a wiki solution, that needs to mail people their passwords.

In the beggining the mail server was returning and advisory to /var/mail/www-data: 

```

...
.b.. while talking to smtp.companydomain.:
>>> MAIL From:<www-data@localmachine.company> SIZE=888
<<< 553 #5.1.8 Domain of sender address <www-data@localmachine.company> does not exist
501 5.6.0 Data format error
...

```

So I did the following config under sendmail.mc:

```
FEATURE(`genericstable',`hash -o /etc/mail/genericstable.db')dnl
GENERICS_DOMAIN_FILE(`/etc/mail/generics-domains')dnl

FEATURE(always_add_domain)dnl
FEATURE(`masquerade_entire_domain')dnl
FEATURE(`masquerade_envelope')dnl
FEATURE(`allmasquerade')dnl

MAILER_DEFINITIONS
MAILER(`local')dnl
MAILER(`smtp')dnl

MASQUERADE_AS(`oi.net.br')dnl
MASQUERADE_DOMAIN(`oi.net.br.')dnl
MASQUERADE_DOMAIN(localhost)dnl
MASQUERADE_DOMAIN(localhost.localdomain)dnl
MASQUERADE_DOMAIN(terj0pra028842.telemar.net.br)dnl
MASQUERADE_DOMAIN(terj0pra028842)dnl
```

And issued the following commands:

make
newaliases
/etc/init.d/sendmail restart

And also created the following files:

oi@localmachine:/etc/mail$ cat generics-domains
localmachine
localmachine.companydomain
companydomain

oi@companydomain:/etc/mail$ cat genericstable
www-data  enrico.luzi@companydomain
root  enrico.luzi@companydomain
oi  enrico.luzi@companydomain

Now I don't receive the advisories anymore, and my mail.log says:

```
Apr 15 19:44:31 localmachine sendmail[16698]: m3FMiGem016698: from=oi, size=72, class=0, nrcpts=1, msgid=<200804152244.m3FMiGem016698@localmachine.company.net.br>, relay=oi@localhost
Apr 15 19:44:31 localmachine sm-mta[16699]: m3FMiVh2016699: from=<oi@localmachine.company.net.br>, size=391, class=0, nrcpts=1, msgid=<200804152244.m3FMiGem016698@localmachine.company.net.br>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Apr 15 19:44:31 localmachine sm-mta[16699]: m3FMiVh2016699: to=<enrico.luzi@companydomain>, ctladdr=<oi@localmachine.company.net.br> (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=esmtp, pri=30391, relay=smtp.companydomain. [200.222.3.99], dsn=2.0.0, stat=Sent (ok:  Message 16044892 accepted)
Apr 15 19:44:31 localmachine sendmail[16698]: m3FMiGem016698: to=enrico.luzi@companydomain, ctladdr=oi (1000/1000), delay=00:00:15, xdelay=00:00:00, mailer=relay, pri=30072, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m3FMiVh2016699 Message accepted for delivery)
```

When I try to mail someone through bash I get:

```
oi@localmachine:~$ mail -v enrico.luzi@companydomain
Subject: test
ssssssssssssssssss
Cc:
enrico.luzi@companydomain... Connecting to [127.0.0.1] port 587 via relay...
220 localmachine.company.corp.net ESMTP Sendmail 8.13.8/8.13.8/Debian-3; Tue, 15 Apr 2008 19:44:31 -0300; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO localmachine.company.net.br
250-localmachine.company.corp.net Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<oi@localmachine.company.net.br> SIZE=72 AUTH=oi@localmachine.company.net.br
250 2.1.0 <oi@localmachine.company.net.br>... Sender ok
>>> RCPT To:<enrico.luzi@companydomain>
>>> DATA
250 2.1.5 <enrico.luzi@companydomain>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
050 <enrico.luzi@companydomain>... Connecting to smtp.companydomain. via esmtp...
050 220 Secure Server ESMTP
050 >>> EHLO localmachine.company.corp.net
050 250-Secure Server
050 250-8BITMIME
050 250 SIZE 10485760
050 >>> MAIL From:<oi@companydomain> SIZE=391
050 250 sender <oi@companydomain> ok
050 >>> RCPT To:<enrico.luzi@companydomain>
050 250 recipient <enrico.luzi@companydomain> ok
050 >>> DATA
050 354 go ahead
050 >>> .
050 250 ok:  Message 16044892 accepted
050 <enrico.luzi@companydomain>... Sent (ok:  Message 16044892 accepted)
250 2.0.0 m3FMiVh2016699 Message accepted for delivery
enrico.luzi@companydomain... Sent (m3FMiVh2016699 Message accepted for delivery)
Closing connection to [127.0.0.1]
>>> QUIT
221 2.0.0 localmachine.company.corp.net closing connection
oi@localmachine:~$
```

And the mail still does not arrive...  What am I doing wrong...

---

### Post by tomasd on 2008-06-16
WRONG
sendmail_path =/usr/sbin/sendmail -t -i [email]-fmailer@yourdomain.com[/email] 
RIGHT
sendmail_path =/usr/sbin/sendmail -t -i -f [email]mailer@yourdomain.com[/email] 

worked for me, thanks!

---

