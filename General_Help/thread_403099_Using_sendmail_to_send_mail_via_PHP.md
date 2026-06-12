---
title: "Using sendmail to send mail via PHP"
date: 2007-04-06
forum: General Help
---

### Post by emil_12 on 2007-04-06
I'm trying to send mail from my webserver (on ubuntu). I've installed sendmail and in my php.ini have I tried to change the sendmail_path but without result. When I'm using mail('blakg..') in PHP the script continue as normal but I get no mail.

When I login via SSH it says you got mail but how do I read them? Has it something to do with my issue?

And how do I get php to send out those emails...

---

### Post by invalid on 2007-04-06
> **emil_12 said:**
> When I login via SSH it says you got mail but how do I read them?

```
mail
```
Or install a client with extra features like mutt, or pine.

---

