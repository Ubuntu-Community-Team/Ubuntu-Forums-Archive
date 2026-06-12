---
title: "change smtp relay server"
date: 2021-07-09
forum: General Help
---

### Post by lacid2 on 2021-07-09
What is the best way to specify a relay server for outgoing emails? I have my own relay server that I'd like to use.

So I can avoid messages like:
[HTML]
/var/log/maillog
Jul  9 19:43:10 myubuntu.hostname.com sm-mta[6089]: 169JhAZw006087: to=<tom@myemail.com>, ctladdr=<tom@myubuntu.hostname.com> (370133/6002), delay=00:00:00, xdelay=00:00:00, mailer=esmtp, pri=120396, relay=alt4.aspmx.l.google.com. [142.250.153.26], dsn=4.0.0, stat=Deferred: Connection refused by alt4.aspmx.l.google.com."[/HTML]

---

### Post by TheFu on 2021-07-09
The relay is set with a single config file line. 
```
relayhost = some.other.hostname-or-IP
```
Just be certain that some.other.hostname-or-IP accepts unauthenticated SMTP from your IP address.  If using a login is required, that's a little harder.  I don't do it that way.

Also, be 100% certain you never run an open relay. That will get your email server blocked by everyone on the internet in a few hours. Getting off those block lists is much harder. Sometimes it can take years.

---

### Post by lacid2 on 2021-07-10
Nice. To which config file should I add the line?

---

### Post by lacid2 on 2021-07-13
I chose this solution:
- install sendmail (in my case it was a better option than postfix)
- add the following line to /etc/mail/sendmail.mc:
[FONT=courier new]"define(`SMART_HOST', `your.smtp.server')dnl" [/FONT]
- make -C /etc/mail reload

---

