---
title: "Mail postfix /etc/aliases.db error"
date: 2004-11-28
forum: General Help
---

### Post by wallijonn on 2004-11-28
When I listed /var/log by "view as list" I noticed syslog, mail.warn, mail.log, mail.info being written into:
```
localhost postfix/local[5035]: fatal: open database /etc/aliases.db: **No such file or directory**
localhost postfix/master[4482]: warning: process /usr/lib/postfix/local pid 5035 exit status 1
localhost postfix/master[4482]: warning: /usr/lib/postfix/local: bad command startup -- throttling 
```
so I
```

#sudo touch /etc/aliases.db
#sudo chmod u+x /etc/aliases.db

```
now I get
```

localhost postfix/local[5822]: fatal: open database /etc/aliases.db: **Bad file descriptor**
localhost postfix/master[4419]: warning: process /usr/lib/postfix/local pid 5822 exit status 1
localhost postfix/master[4419]: warning: /usr/lib/postfix/local: bad command startup -- throttling

```

I am using Evolution and it is working fine. How do I stop the "root" account from trying to send usermail? (That's what I am assuming it is trying to do).

What can I say?, I don't like seeing the word "throttling" in an error log.

[COLOR=DarkGreen]SPM -> postfix -> removal[/COLOR] is not an option as it will remove [COLOR=DarkGreen]ubuntu-base[/COLOR]. 

I've had to 
```

# sudo postfix stop

```
But is this enough?

How do I set a LOCAL_RECIPIENT?

[edit]
I've had to use "Sendmail" as the Sending Mail server type in Evolution to send mail as it will not send mail if I use SMTP Sending Mail server type. Which means that I had to restart / start postfix. 

.

---

### Post by wallijonn on 2004-12-01
```

#[COLOR=Red]cd /etc[/COLOR]
#[COLOR=Red]postfix stop[/COLOR]
#[COLOR=Red]newaliases[/COLOR]
#[COLOR=Red]postfix start[/COLOR]
#[COLOR=Red]exit[/COLOR]

```

---

