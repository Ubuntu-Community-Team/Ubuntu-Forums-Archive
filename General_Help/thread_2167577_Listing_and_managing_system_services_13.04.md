---
title: "Listing and managing system services 13.04"
date: 2013-08-14
forum: General Help
---

### Post by denysonique on 2013-08-14
How can I list all system services?
How can I list all running system services?
How do I add/remove services from running?

---

### Post by steeldriver on 2013-08-14
It depends exactly what you mean by "system services", but for services that are managed by traditional init scripts you can use

```
service --status-all
```

If you want to filter out services whose status can't be determined (the ones listed as '[ ? ]'), you can send stderr to null

```
service --status-all 2>/dev/null
```

If you want to list only running services

```
service --status-all 2>/dev/null | grep -w '+'
```

For services managed via the upstart mechanism you can use 'initctl' (you can pipe the output to grep if you want to filter out running /non-running)

```
initctl list
```

Likewise, adding/removing services would depend on whether they are upstart jobs or traditional init scripts, it's beyond my expertise so I'll let someone else answer that in detail

---

### Post by denysonique on 2013-08-14
Why does Ubuntu have two startup systems at the same time? Isn't it a mess. At least there should be a single command line tool to manage all system services.

---

