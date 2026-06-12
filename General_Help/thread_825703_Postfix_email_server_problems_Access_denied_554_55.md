---
title: "Postfix email server problems Access denied 554 554 5.7.1 state 14"
date: 2008-06-11
forum: General Help
---

### Post by AceRiImmer on 2008-06-11
Hi,

I've been having troubles with this for days and can't get anywhere with it.

My server ip is: 77.92.85.11
Mail server: mail.spam.com

When i try sending an email to anything like, [email]root@spams.com[/email] I get:

```
Technical details of permanent failure:
PERM_FAILURE: Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 554 554 5.7.1 <root@spam.com>: Recipient address rejected: Access denied (state 14).
```

Here is what /var/log/mail.info looks like, its full of entries like this:
```

Jun 11 10:43:02 server31010 postfix/qmgr[30611]: 8F9C92E4F23: from=<root@mail.spam.com>, size=662, nrcpt=1 $
Jun 11 10:43:28 server31010 postfix/local[30613]: fatal: open database /etc/aliases.db: No such file or dire$
Jun 11 10:43:29 server31010 postfix/master[31403]: warning: process /usr/lib/postfix/local pid 30613 exit st$
Jun 11 10:43:29 server31010 postfix/master[31403]: warning: /usr/lib/postfix/local: bad command startup -- t$
Jun 11 10:44:01 server31010 postfix/pickup[30537]: DD7B42E5066: uid=0 from=<root>


```

Let me know what files i need to show to help me fix this nightmare.

I'm a complete novice so help will be greatly appreciated :)

---

