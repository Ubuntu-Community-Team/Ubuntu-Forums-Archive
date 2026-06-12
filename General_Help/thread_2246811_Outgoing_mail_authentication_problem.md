---
title: "Outgoing mail authentication problem"
date: 2014-10-03
forum: General Help
---

### Post by JKyleOKC on 2014-10-03
I'm in the process of replacing a working 12.04.5 system with a clean install of Xubuntu 14.04.1, on a separate drive so that both systems are available while setting up configurations. At the moment I have just one critical problem.

My ISP, AT&T, blocks port 25 so that in order to send mail from my local Postfix/Dovecot server, I must relay through my gmail account via port 587. This has worked perfectly for quite some time on the old system. However on the new one, any attempt to send a test message results in this, from /var/log/mail.log:```
Oct  2 18:40:27 mehitabel postfix/smtpd[4540]: connect from unknown[192.168.0.2]
Oct  2 18:40:27 mehitabel postfix/smtpd[4540]: B356DC24FB: client=unknown[192.168.0.2], sasl_method=PLAIN, sasl_username=jk
Oct  2 18:40:27 mehitabel postfix/cleanup[4545]: B356DC24FB: message-id=<542DE26A.80002@--MyServer-->
Oct  2 18:40:27 mehitabel postfix/qmgr[1984]: B356DC24FB: from=<jk@--MyServer-->, size=600, nrcpt=1 (queue active)
Oct  2 18:40:27 mehitabel postfix/smtpd[4540]: disconnect from unknown[192.168.0.2]
Oct  2 18:40:28 mehitabel postfix/smtp[4546]: B356DC24FB: to=<pub@--MyServer-->, relay=smtp.gmail.com[64.233.160.108]:587, delay=0.59, delays=0.03/0.02/0.49/0.05, dsn=5.5.1, **status=bounced (host smtp.gmail.com[64.233.160.108] said: 530-5.5.1 Authentication Required. Learn more at 530 5.5.1 http://support.google.com/mail/bin/answer.py?answer=14257 i1sm3270984oew.6 - gsmtp (in reply to MAIL FROM command)**)
Oct  2 18:40:28 mehitabel postfix/cleanup[4545]: 63FF0C250C: message-id=<20141002234028.63FF0C250C@jimkyle.dns2go.com>
Oct  2 18:40:28 mehitabel postfix/bounce[4547]: B356DC24FB: sender non-delivery notification: 63FF0C250C
Oct  2 18:40:28 mehitabel postfix/qmgr[1984]: 63FF0C250C: from=<>, size=2730, nrcpt=1 (queue active)
Oct  2 18:40:28 mehitabel postfix/qmgr[1984]: B356DC24FB: removed
Oct  2 18:40:29 mehitabel postfix/smtp[4546]: 63FF0C250C: to=<jk@--MyServer-->, relay=smtp.gmail.com[64.233.160.109]:587, delay=0.55, delays=0.03/0/0.47/0.05, dsn=5.5.1, **status=bounced (host smtp.gmail.com[64.233.160.109] said: 530-5.5.1 Authentication Required. Learn more at 530 5.5.1 http://support.google.com/mail/bin/answer.py?answer=14257 ls8sm3311493obb.13 - gsmtp (in reply to MAIL FROM command)**)
Oct  2 18:40:29 mehitabel postfix/qmgr[1984]: 63FF0C250C: removed
```The 192.168.0.2 address is the local machine from which I attempted to send a test message to myself at my public address.

All communication to and from my public address is working properly. Only attempts to route outgoing traffic from my local server to gmail receive the bounce action, and it shows up **only** in the log file.

My initial searching for solutions led me to do a "diff" between the old and new versions of the various configuration files (copied to a "work" directory so that I could modify their names and identify which was which). The only differences I see are in the /etc/postfix/master.cf file, as follows:```
*jk@mehitabel:~/work$* diff "old master.cf" "new master.cf" 
3c3,4
< # of the file, see the master(5) manual page (command: "man 5 master").
---
> # of the file, see the master(5) manual page (command: "man 5 master" or
> # on-line: http://www.postfix.org/master.5.html).
12c13
< pickup    **fifo**  n       -       -       60      1       pickup
---
> pickup    **unix**  n       -       -       60      1       pickup
14c15
< qmgr      **fifo**  n       -       n       300     1       qmgr
---
> qmgr      **unix**  n       -       n       300     1       qmgr
27d26
**< 	-o smtp_fallback_relay=**
*jk@mehitabel:~/work$ *

```I suspect that the option line (last one in the diff output) that's in the old file but not in the new just may be the problem, but I'd like some confirmation before making any changes, since everything is working from my public servers and I don't want to risk disabling access to them!

---

### Post by JKyleOKC on 2014-10-05
Bump!

I tried adding the option line in main.cf but it had no effect on the problem.

Almost a year ago I had a similar problem and solved it as related in [http://ubuntuforums.org/showthread.php?t=2186760&p=12846081&viewfull=1#post12846081](http://ubuntuforums.org/showthread.php?t=2186760&p=12846081&viewfull=1#post12846081) -- but that solution is already in place so this problem must be something different.

I did add debug logging to my master.cf file, and here's what I believe to be the critical part of a failed attempt:```
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: [COLOR="#FF0000"]Untrusted TLS connection established to smtp.gmail.com[/COLOR][74.125.198.108]:587: TLSv1.2 with cipher ECDHE-RSA-AES128-GCM-SHA256 (128/128 bits)
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: smtp_stream_setup: maxtime=300 enable_deadline=0
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: > smtp.gmail.com[74.125.198.108]:587: EHLO jimkyle.dns2go.com
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 250-mx.google.com at your service, [162.227.43.140]
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 250-SIZE 35882577
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 250-8BITMIME
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 250-AUTH LOGIN PLAIN XOAUTH XOAUTH2 PLAIN-CLIENTTOKEN
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 250-ENHANCEDSTATUSCODES
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 250-PIPELINING
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 250-CHUNKING
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 250 SMTPUTF8
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: server features: 0x100f size 35882577
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: Using ESMTP PIPELINING, TCP send buffer size is 87040, PIPELINING buffer size is 4096
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: smtp_stream_setup: maxtime=300 enable_deadline=0
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: > smtp.gmail.com[74.125.198.108]:587: MAIL FROM:<jk@jimkyle.com> SIZE=597
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: > smtp.gmail.com[74.125.198.108]:587: RCPT TO:<pub@jimkyle.com>
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: > smtp.gmail.com[74.125.198.108]:587: DATA
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: smtp_stream_setup: maxtime=300 enable_deadline=0
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: [COLOR="#FF0000"]530-5.5.1 Authentication Required.[/COLOR] Learn more at
Oct  4 23:06:12 mehitabel postfix/smtp[28816]: < smtp.gmail.com[74.125.198.108]:587: 530 5.5.1 http://support.google.com/mail/bin/answer.py?answer=14257 fj8sm7556782obc.10 - gsmtp

```Perhaps the "untrusted" part of the connection is the key, but I'm at a loss as to how to make the connection trusted. Hopefully some of those who were so helpful a year ago (such as SeijiSensei and TheFu) will jump in with some ideas...

I do have the complete log from that failed test if it's needed; I just felt it best to cut it down to the critical area (or what I think is that area).

---

### Post by cigtoxdoc on 2014-10-05
If you outbound e-mail server is outbound.att.net then you should not be using Port 25, but Port 465.  I have absolutely no problems with Evolution 3.10.4 sending and receiving from AT&T.

John

---

### Post by JKyleOKC on 2014-10-05
> **cigtoxdoc said:**
> If you outbound e-mail server is outbound.att.net then you should not be using Port 25, but Port 465.  I have absolutely no problems with Evolution 3.10.4 sending and receiving from AT&T.No, the outbound server involved is a local one, Postfix. I do not use either the AT&T/Yahoo email service, or Evolution. And my public email services are all working properly.

This problem is that a private mail server, which cannot use port 25 because that is blocked by AT&T for all Uverse accounts, is unable to authenticate properly to the gmail account that I have used as a relay for the past 11 months although all of my server configuration files appear to still be the same.

Thanks for responding, though!

---

### Post by JKyleOKC on 2014-10-06
Finally solved, and it was simple -- once I realized that the "*smtpd*" lines in main.cf are for **incoming** traffic only, while **outgoing** traffic is configured by almost-identical "*smtp*" lines! Adding these six lines to main.cf, then reloading the configuration, made everything work properly:```
#added 3 Oct 2014 - jk
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtp_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```
Only remaining question is why did it work on the old system; perhaps the two directions weren't handled separately in the version from 2012...

---

