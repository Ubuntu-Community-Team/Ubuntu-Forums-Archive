---
title: "Will setting an IMAP separator break existing users email folders?"
date: 2013-11-27
forum: General Help
---

### Post by terryit3 on 2013-11-27
I have users using Squirrelmail, and a few users using Thunderbird to access their work email.  I am upgrading from the old-school version of Squirrelmail to RoundCube. RoundCube requires an IMAP separator be set in order to create subfolders within their email. I think SM might as well, but this was never a requested addition, so I never looked into it.

In my dovecot.conf file, if I change the separator line from 
```
#separator =  
```
to 
```
separator = /
``` 
will this break anything in my users accounts?

The separator was never set up and a lot of users have years worth of email built-up.  I am running Dovecot and Sendmail on Ubuntu 10.04.

Thanks for any help

---

### Post by terryit3 on 2013-11-29
Still looking for an answer..

---

### Post by terryit3 on 2013-12-03
This is my last bump.

---

