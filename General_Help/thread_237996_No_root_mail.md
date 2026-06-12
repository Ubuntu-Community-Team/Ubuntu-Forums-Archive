---
title: "No root mail?"
date: 2006-08-17
forum: General Help
---

### Post by Anduu on 2006-08-17
Before I did a fresh install of Dapper I used to get root's system mail forwarded to my user account so I could keep tabs on stuff.

Just tonight I decided to get it all set up again however now root doesn't get any mail at all.There isn't even a root folder in /var/mail.

The only thing I have done differently this time around is I have opted to use postfix rather than sendmail...does sendmail have something to do with sending system messages to root@localhost?If so can postfix be configured to do this?

I dunno...I must be missing something...I thought by default system messages were sent to root's mail.

Any insights?

---

### Post by peabody on 2006-08-17
1) Check that postfix is running.

2) What does /etc/aliases say?

---

### Post by Anduu on 2006-08-17
If I Do a sudo postfix start it says postfix already running.

My /etc/aliases

```
# Added by installer for initial user
root:	anduu
clamav: root
```

---

### Post by mlind on 2006-08-17
Try adding postmaster too
```

postmaster:    root

```

Reconfiguring postfix may help too (it generates funny /etc/aliases file..)
```

sudo dpkg-reconfigure postfix

```

---

### Post by Anduu on 2006-08-17
Okey I did a sudo dpkg-reconfigure postfix...I don't recall going through the setup process when I installed postfix.

To test things out I sent an email to root@localhost then went to /var/mail to see if it worked and it did;but not how I thought it would.

Rather than a file called "root" in var mail there is "anduu" and the test email is in there along with a couple others addressed to "root@localhost".So I guess I don't need to worry about editing /root/.forward ?

Just to make sure /etc/aliases is OK here it is...I deleted the original because during the postfix setup it said it can only modify a new /etc/aliases.
I put "root:   anduu" and "clamav: root" back in as I am assuming they were in there for a reason?


```
# See man 5 aliases for format
postmaster:    root
root:	/var/mail
postmaster:	/var/mail
root:	anduu
clamav: root

```

Anyway let me know if anything doesn't look right.

Thanx :)

---

### Post by Anduu on 2006-08-17
Oh man back to square one...

Shortly afterwards my test emails started coming back saying they were undeliverable.I figured I had chosen an improper setting so I tried in vain to get it workingagain .I even uninstalled/reinstalled postfix and nothing.

I am now back at the stage of having no root mail in /var/mail and nothing I do now brings it back.

I am completely lost ](*,) 

My alisase file is still the same as my last post

---

### Post by peabody on 2006-08-18
> **Anduu said:**
> Oh man back to square one...

Shortly afterwards my test emails started coming back saying they were undeliverable.I figured I had chosen an improper setting so I tried in vain to get it workingagain .I even uninstalled/reinstalled postfix and nothing.

I am now back at the stage of having no root mail in /var/mail and nothing I do now brings it back.

I am completely lost ](*,) 

My alisase file is still the same as my last post

I have zero experience setting up postfix.  It does sound quite frustrating.  Just a couple of things...

1) Who are your test emails addressed to?  Another user on the same box or to some address on the Internet?
2) I know with sendmail and company you need to run "newaliases" as root and restart the mail service for the new aliases to take effect.

And just to double check (not trying to insult your intelligence here, I'm pretty sure you know this) "anduu" is your username on the box correct?

---

### Post by mlind on 2006-08-18
I'm not sure how you want your mail delivered, but this is what I use for simple setup
```

postmaster:    root
root: mlind

```
All system mail is stored on /var/mail/mlind


> 
The user root (and any other users with a uid of 0) must have mail
redirected via an alias, or their mail may be delivered to
/var/mail/nobody.  This is by design:  mail is not delivered to external
delivery agents as root.


If you want root to recieve mail too, don't include alias definition
```

root: anduu

```

---

### Post by Anduu on 2006-08-18
> **peabody said:**
> I have zero experience setting up postfix.  It does sound quite frustrating.  Just a couple of things...

1) Who are your test emails addressed to?  Another user on the same box or to some address on the Internet?
2) I know with sendmail and company you need to run "newaliases" as root and restart the mail service for the new aliases to take effect.

And just to double check (not trying to insult your intelligence here, I'm pretty sure you know this) "anduu" is your username on the box correct?

1. I am mailing to root@localhost

2. When you reconfigure postfix it automatically runs newaliases and restarts.

...and yup anduu is my username ;)

---

### Post by Anduu on 2006-08-18
OK an update...After many many tries reconfiguring post fix I am here...

I now have a file in /var/mail called "nobody" with the following contents:
```
From smmsp@localhost  Fri Aug 18 20:00:01 2006
Return-Path: <smmsp@localhost>
X-Original-To: root
Delivered-To: root@localhost
Received: by localhost (Postfix, from userid 111)
	id ACCA55CC30A; Fri, 18 Aug 2006 20:00:01 -0600 (MDT)
From: root@localhost (Cron Daemon)
To: root@localhost
Subject: Cron <smmsp@AthlonXP2200PlusViaASUS> test -x /usr/share/sendmail/sendmail && /usr/share/sendmail/sendmail cron-msp
X-Cron-Env: <MAILTO=root>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/var/lib/sendmail>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=smmsp>
Message-Id: <20060819020001.ACCA55CC30A@localhost>
Date: Fri, 18 Aug 2006 20:00:01 -0600 (MDT)

/usr/share/sendmail/sendmail: line 826: /usr/sbin/sendmail-msp: No such file or directory
```
...I was trying out sendmail again but remembered that bug it has at boot so I removed it.That is why I suspect that message is there.

And a file called "smmsp" containing:
```
From MAILER-DAEMON  Fri Aug 18 20:20:01 2006
Return-Path: <>
X-Original-To: smmsp@localhost
Delivered-To: smmsp@localhost
Received: by localhost (Postfix)
	id 89F945CC30B; Fri, 18 Aug 2006 20:20:01 -0600 (MDT)
Date: Fri, 18 Aug 2006 20:20:01 -0600 (MDT)
From: MAILER-DAEMON@localhost (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: smmsp@localhost
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
	boundary="780D15CC30A.1155954001/localhost"
Message-Id: <20060819022001.89F945CC30B@localhost>

This is a MIME-encapsulated message.

--780D15CC30A.1155954001/localhost
Content-Description: Notification
Content-Type: text/plain

This is the Postfix program at host localhost.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

			The Postfix program

<root@localhost> (expanded from <root>): maildir delivery failed: create
    /var/mail/tmp/1155954001.P12424.localhost: Permission denied

--780D15CC30A.1155954001/localhost
Content-Description: Delivery report
Content-Type: message/delivery-status

Reporting-MTA: dns; localhost
X-Postfix-Queue-ID: 780D15CC30A
X-Postfix-Sender: rfc822; smmsp@localhost
Arrival-Date: Fri, 18 Aug 2006 20:20:01 -0600 (MDT)

Final-Recipient: rfc822; root@localhost
Original-Recipient: rfc822; root
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; maildir delivery failed: create
    /var/mail/tmp/1155954001.P12424.localhost: Permission denied

--780D15CC30A.1155954001/localhost
Content-Description: Undelivered Message
Content-Type: message/rfc822

Received: by localhost (Postfix, from userid 111)
	id 780D15CC30A; Fri, 18 Aug 2006 20:20:01 -0600 (MDT)
From: root@localhost (Cron Daemon)
To: root@localhost
Subject: Cron <smmsp@AthlonXP2200PlusViaASUS> test -x /usr/share/sendmail/sendmail && /usr/share/sendmail/sendmail cron-msp
X-Cron-Env: <MAILTO=root>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/var/lib/sendmail>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=smmsp>
Message-Id: <20060819022001.780D15CC30A@localhost>
Date: Fri, 18 Aug 2006 20:20:01 -0600 (MDT)

/usr/share/sendmail/sendmail: line 826: /usr/sbin/sendmail-msp: No such file or directory

--780D15CC30A.1155954001/localhost--
```



My /etc/aliases:
```
# See man 5 aliases for format
postmaster:    root
root:	/var/mail/
postmaster:	/var/mail/
```

My /etc/postfix/man.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.1
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all
```

Should I include any other info?

Anywho it seems to be doing something now...I just think something ain't right.My brain is fried :???:

---

### Post by Anduu on 2006-08-19
OK OK I finally got it to work...not sure how exactly but I did it :p

Basically just used a few hours worth of trial and error reconfiguring.

I think mlind's simple alias had a lot to do with it...once I changed mine and reconfigured again using some slightly different options it was all good.

Anywho thanks for the help :)

---

