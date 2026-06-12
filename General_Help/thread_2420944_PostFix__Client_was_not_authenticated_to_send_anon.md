---
title: "PostFix:  Client was not authenticated to send anonymous mail during MAIL FROM"
date: 2019-06-13
forum: General Help
---

### Post by josephmmorgan on 2019-06-13
First, I'll admit I don't really know what I'm doing.  I'm following a bunch of posts here and there but cannot figure out how to get my server to send mail via SMTP PostFix.

I believe the problem is that when it sends the email, I can see in the mail.log file the following output:

```

Jun 13 10:54:52 DellR710-1 postfix/qmgr[11547]: 5E00C2080BB3: from=<myServerUserName@myServerHostName>, size=421, nrcpt=1 (queue active)
Jun 13 10:54:52 DellR710-1 postfix/smtp[11594]: Host offered STARTTLS: [smtp.office365.com]
Jun 13 10:54:57 DellR710-1 postfix/smtp[11594]: 5E00C2080BB3: to=<someone@someplace.com>, relay=smtp.office365.com[40.97.120.210]:587, delay=5.1, delays=0.02/0.01/0.07/5, dsn=5.7.57, status=bounced (host smtp.office365.com[40.97.120.210] said: 530 5.7.57 SMTP; Client was not authenticated to send anonymous mail during MAIL FROM [SN4PR0701CA0030.namprd07.prod.outlook.com] (in reply to MAIL FROM command))

```

So, I think the problem is that in the "from", it is building a fake email address composed of my user name on my server and the host name of my server (from=<myServerUserName@myServerHostName>).  I need the "from" to be built from a valid email at my valid domain.  For the life of me I can't get it to change.

I have the following in my sasl_password file:

```
smtp.office365.com:587 myOffice365UserName@myOffice365.domain:myOffice365Password
```

In my /etc/postfix/generic file, I have:

```
myServerUserName@myServerHostName myOffice365UserName@myOffice365.domain
```

I've done all the service postmaps and postfix restarts for these, and have the appropriate (I think) entries in my main.cf:

```

smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
smtp_sasl_security_options = noanonymous
smtp_generic_maps = hash:/etc/postfix/generic

relayhost = smtp.office365.com:587

```


But when I send an email, I get:

> SMTP; Client was not authenticated to send anonymous mail during MAIL FROM [SN4PR0701CA0030.namprd07.prod.outlook.com] (in reply to MAIL FROM command))


Edit:  So I used "sendmail" to send an email and was able to get it to use my true email address as the "from" address, but I still get the same error.  I clearly don't understand the error message.  Can someone tell me how it is the email is being sent anonymously??  Especially considering I've setup everything to authorize properly (according to everything Google can give me).

---

