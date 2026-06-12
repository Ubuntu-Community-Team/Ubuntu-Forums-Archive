---
title: "iptables logging then dropping traffic"
date: 2018-05-06
forum: General Help
---

### Post by sniper8752 on 2018-05-06
I just want to make sure I understand this correctly.  If I set the default policy of INPUT/OUTPUT, etc. to the chain, logging, then have that set to log/drop traffic, is this the same thing as just setting the default policy as drop?  I want to make sure I am not overlooking something, and somehow the invalid traffic gets through.

---

### Post by SeijiSensei on 2018-05-06
I usually leave the default INPUT policy as ACCEPT then include these two lines at the bottom of the ruleset:
```

/sbin/iptables -A INPUT -j LOG --log-prefix=unhandled_traffic
/sbin/iptables -A INPUT -j REJECT

```

---

