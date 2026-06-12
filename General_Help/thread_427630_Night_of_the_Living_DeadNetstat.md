---
title: "Night of the Living Dead/Netstat"
date: 2007-04-29
forum: General Help
---

### Post by reclusivemonkey on 2007-04-29
Has anyone else been attacked by Zombies? I noticed the other day I had a Zombie netstat on my system. It seemed to appear every day, so I grepped for netstat in /etc and found this;

```

/etc/bash_completion:#for i in env netstat seq uname units wget; do

```

I commented out the relevant loop in bash_completion and my zombie is gone! Anyone else get this?

---

