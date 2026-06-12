---
title: "sSMTP mail to root (or localuser)"
date: 2015-06-14
forum: General Help
---

### Post by kendallp on 2015-06-14
I have sSMTP setup and can send mail to a specified e-mail address without any issue.  For example:

```
echo "test message" | mail -s 'Test' kendallp@hotmail.com
```

But if I try to send mail to a user (e.g. root) ```
echo "test message" | mail -s 'Test' root
``` it uses my hostname as the domain so the mail never goes though because of an invalid domain name in the "To:" field.

sSMTP doesn't use /etc/aliases but I found the following suggestion [http://possiblelossofprecision.net/?p=591]("http://possiblelossofprecision.net/?p=591") which said I needed to create a /etc/mail.rc file.  That didn't work and then from the very bottom comment on that page said that it should instead be /etc/nail.rc which didn't work either. 

Does anyone else have a suggestion?   



My config files are below:


/etc/ssmtp/ssmtp.conf:
```
cat /etc/ssmtp/ssmtp.conf
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=kendallp@hotmail.com

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.mandrillapp.com:587

AuthUser=kendallp@hotmail.com
AuthPass=mypassword
UseTLS=YES
UseSTARTTLS=YES

# Where will the mail seem to come from?
rewriteDomain=hotmail.com

# The full hostname
hostname=kendallp@hotmail.com

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES

Debug=YES
```

/etc/ssmtp/revaliases:
```
cat /etc/ssmtp/revaliases
# sSMTP aliases
#
# Format:       local_account:outgoing_address:mailhub
#
# Example: root:your_login@your.domain:mailhub.your.domain[:port]
# where [:port] is an optional port number that defaults to 25.
root:kendallp@hotmail.com:smtp.mandrillapp.com:587
test:kendallp@hotmail.com:smtp.mandrillapp.com:587
```


```
# tail -n 100 /var/log/syslog
Jun 14 13:39:49 NAS sSMTP[1717]: Set MailHub="smtp.mandrillapp.com"
Jun 14 13:39:49 NAS sSMTP[1717]: via SMTP Port Number="587"
Jun 14 13:39:49 NAS sSMTP[1717]: Creating SSL connection to host
Jun 14 13:39:49 NAS sSMTP[1717]: 220 smtp.mandrillapp.com ESMTP
Jun 14 13:39:49 NAS sSMTP[1717]: EHLO kendallp@hotmail.com
Jun 14 13:39:49 NAS sSMTP[1717]: 250 8BITMIME
Jun 14 13:39:49 NAS sSMTP[1717]: STARTTLS
Jun 14 13:39:49 NAS sSMTP[1717]: 220 2.0.0 Ready to start TLS
Jun 14 13:39:50 NAS sSMTP[1717]: SSL connection using RSA_AES_128_CBC_SHA1
Jun 14 13:39:50 NAS sSMTP[1717]: EHLO kendallp@hotmail.com
Jun 14 13:39:50 NAS sSMTP[1717]: 250 8BITMIME
Jun 14 13:39:50 NAS sSMTP[1717]: AUTH LOGIN
Jun 14 13:39:50 NAS sSMTP[1717]: 334 VXNlcm5hbWU6
Jun 14 13:39:50 NAS sSMTP[1717]: a3BwMzM2MDJAaG90bWFpbC5jb20=
Jun 14 13:39:50 NAS sSMTP[1717]: 334 UGFzc3dvcmQ6
Jun 14 13:39:50 NAS sSMTP[1717]: VU1fMmVERHF0QWFKRy1MX0ZWNkdFQQ==
Jun 14 13:39:50 NAS sSMTP[1717]: 235 2.7.0 Authentication successful
Jun 14 13:39:50 NAS sSMTP[1717]: MAIL FROM:<kendallp@hotmail.com>
Jun 14 13:39:50 NAS sSMTP[1717]: 250 2.1.0 Ok
Jun 14 13:39:50 NAS sSMTP[1717]: RCPT TO:<root@NAS.home>
Jun 14 13:39:50 NAS sSMTP[1717]: 250 2.1.5 Ok
Jun 14 13:39:50 NAS sSMTP[1717]: DATA
Jun 14 13:39:50 NAS sSMTP[1717]: 354 End data with <CR><LF>.<CR><LF>
Jun 14 13:39:50 NAS sSMTP[1717]: Received: by kendallp@hotmail.com (sSMTP sendmail emulation); Sun, 14 Jun 2015 13:39:49 -0400
Jun 14 13:39:50 NAS sSMTP[1717]: From: "root" <root@NAS.home>
Jun 14 13:39:50 NAS sSMTP[1717]: Date: Sun, 14 Jun 2015 13:39:49 -0400
Jun 14 13:39:50 NAS sSMTP[1717]: Subject: root
Jun 14 13:39:50 NAS sSMTP[1717]: To: <root@NAS.home>
Jun 14 13:39:50 NAS sSMTP[1717]: X-Mailer: mail (GNU Mailutils 2.99.98)
Jun 14 13:39:50 NAS sSMTP[1717]:
Jun 14 13:39:50 NAS sSMTP[1717]: root
Jun 14 13:39:51 NAS sSMTP[1717]: .
Jun 14 13:39:51 NAS sSMTP[1717]: 250 2.0.0 Ok: queued as 0F73228020E
Jun 14 13:39:51 NAS sSMTP[1717]: QUIT
Jun 14 13:39:51 NAS sSMTP[1717]: 221 2.0.0 Bye
Jun 14 13:39:51 NAS sSMTP[1717]: Sent mail for kendallp@hotmail.com (221 2.0.0 Bye) uid=0 username=root outbytes=425
```



Thank you,
Kendall

---

### Post by kendallp on 2015-06-16
bump

---

### Post by mastablasta on 2015-06-16
I think root is sending to email. i.e. when service send email to root what will actually happen is root will send email to the designated user's email. handy for getting various reports on status of services etc.

---

