---
title: "weird t-bird, gmail issue"
date: 2006-10-18
forum: General Help
---

### Post by moore.bryan on 2006-10-18
[I]specific details
dapper, openbox, kernel 2.6.15.27-686, cable internet

did a clean install of dapper, installed thunderbird, downloaded my messages.  tweaked iceweasel for speed (disabled ipv6 and set all the networking-pipelining stuff).  

went back the next day, gmail times out in t-bird and has been doing that ever since, not letting me access any emails.  i re-enabled ipv6 just in case that was the issue, didn't know why it would be, and it still doesn't work.  at work, my t-bird downloads just fine... 

any ideas?[/I]

---

### Post by moore.bryan on 2006-10-21
*no one?  i've tried it with sylpheed too and it's on and off... help?*

---

### Post by moore.bryan on 2006-10-26
*well, i (somewhat) answered it myself.  for some mysterious reason, my iptables rule allowing 995 is over-written every startup by peerguardnf.  doesn't make sense why, but that's just how it is.*

---

