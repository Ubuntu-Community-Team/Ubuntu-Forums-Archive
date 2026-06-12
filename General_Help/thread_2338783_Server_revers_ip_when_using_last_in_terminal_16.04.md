---
title: "Server revers ip when using last in terminal 16.04 ubuntu server"
date: 2016-10-01
forum: General Help
---

### Post by chrjoh-88 on 2016-10-01
Hi there my first post here been lurking for a few years, don't really know what I've manage to do here. I've been using som hardening tips and now when I login with ssh this is the output

```
Last login: Sun Oct  2 01:12:50 2016 from c-xxxxxx-xxx-xxxxxxx.cust.bredbandsbolaget.se
```

instead of the ip when i promt in terminal last it's there also, checked /var/log/auth.log and there is my xx.xxx.xxx.xxx ip present.

Any idea what I've mange to do here ?

I've manage to solve it used last | tac and remember that it's called reversed DNS lookup and the fault was in /etc/ssh/sshd_config | usedns yes that was the culprit

---

