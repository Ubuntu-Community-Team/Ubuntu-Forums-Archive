---
title: "alternative to mail and MTA, similar to Send-MailMessage"
date: 2017-03-24
forum: General Help
---

### Post by garlorsus on 2017-03-24
hi,
on windows/powershell I do
Send-MailMessage -From $From -to $To -Cc $Cc -Subject $Subject `-Body  $Body -SmtpServer $SMTPServer -port $SMTPPort -UseSsl -Attachments  $Attachment

is there any similar command for ubuntu which doesn't need an MTA like posfix/sendmail/exim to just send an email to a smtp relay?

---

### Post by r.stiltskin on 2017-03-24
You should already have s-nail installed (and /usr/bin/mail linking to it).

Install (if you don't already have it) msmtp and set up a configuration file ~/.msmtprc to configure it to your smtp account, e.g.:```

# .msmtprc     ##configuration file for msmtp

#account     [account name of your choosing]
host         [smtp server]
from         [username@server]
auth         login
tls          off
user         [email username]
password     [email password]
port         587

#account default : [account name of your choosing]
```

Configure ~/.mailrc to set msmtp as the smtp client, e.g.```
set sendmail=/usr/bin/msmtp

```
Here are two ways to send:
```

echo "CONTENT OF MESSAGE" | mail -s "SUBJECT LINE" [RECIPIENT]
```
or create a file containing subject and message, for example, ~/message.txt containing:```

Subject: [SUBJECT LINE]

[CONTENT OF MESSAGE]
```
and then run
```

cat ./message.txt | msmtp [RECIPIENT]
```

---

### Post by garlorsus on 2017-03-24
I've explicitly asked for an alternative to mail and MTA, and you end up telling me to use mail and an MTA, thx but no thx

---

### Post by r.stiltskin on 2017-03-24
I mentioned s-nail for completeness, since it requires virtually no configuration.

But actually I also gave you an alternative that doesn't use s-nail, using msmtp directly.  Maybe you didn't read that far.  

You're welcome.

---

### Post by garlorsus on 2017-03-24
send-mailmessage allows me to insert all the data on the same command, while mail doesn't allow me to change the "from" or the smtp server and it's configuration to send each mail, if that were the case I could use it
if I use mail, mail will send it always using the same smtp server and the same from ( which are configured on snail/msmtp ), which I don't want, if you can tell me how to change this I will be happy to use it

---

