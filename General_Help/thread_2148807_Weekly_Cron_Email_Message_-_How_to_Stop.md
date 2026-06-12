---
title: "Weekly Cron Email Message - How to Stop?"
date: 2013-05-26
forum: General Help
---

### Post by JeffWalden on 2013-05-26
In my mail server log I'm seeing the following message every week:

```
Dropped: root@admin &#8594; root@admin 'Cron <root@development> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )' No MX for [admin]
```

That being said, I have no idea where this cron job is coming from that is generating an email message. Where can I look to track this down and ultimately put a stop to it?

---

