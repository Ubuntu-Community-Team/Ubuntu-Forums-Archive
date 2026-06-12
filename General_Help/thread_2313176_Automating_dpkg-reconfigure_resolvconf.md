---
title: "Automating dpkg-reconfigure resolvconf"
date: 2016-02-10
forum: General Help
---

### Post by andre-mamelund on 2016-02-10
Hi,

I've built a linux image that's going to be installed on multiple computers. What I've noticed is that /etc/resolv.conf is missing.

When I run dpkg-reconfigure resolvconf and answer Yes then Ok inside the graphics the resolv.conf file gets created and everything is working fine.

I need a way of automating the input without the person having to press Yes then Ok.

I've spent quite a while googling and checking the man pages but haven't found a solution.

Tried to change the dpkg interface to readline then use yes command. Doesn't work.
**yes | dpkg-reconfigure -f readline resolvconf**

Thanks,
Andre

---

### Post by andre-mamelund on 2016-02-10
Posting my solution if anyone should every google something similar. The lines below I have inside of a more complex bash script.

```
/usr/bin/expect<<EOF
spawn dpkg-reconfigure -f readline resolvconf
expect "updates?" { send "Yes\r" }
expect "dynamic files?" { send "Yes\r" }
EOF
```

---

