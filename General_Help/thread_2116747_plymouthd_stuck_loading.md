---
title: "plymouthd stuck loading"
date: 2013-02-16
forum: General Help
---

### Post by nondescriptpenguin on 2013-02-16
Hello there. About 20 minutes ago I decided to configure a vpn in my network connections. Everything seemed to setup fine so I restarted per some instructions. I go to boot up again and suddenly the ubuntu loading screen is as far as my system will boot. I was able to get into tty2 and found that plymouthd was likely my problem as it was the highest resource user in top. A quick search let me know that this was what initiated the ubuntu gui. I did a strace on the process and as far as I am able to tell, the process is stuck trying to retrieve the time:

~# strace -p 263
clock_getting(CLOCK_MONOTONIC, {717, 827819110}) = 0
clock_getting(CLOCK_MONOTONIC, {717, 830163198}) = 0
clock_getting(CLOCK_MONOTONIC, {717, 832521951}) = 0
epoll_wait(3, {}, 64, 2)                         = 0

(Continue this sequence in increments for all eternity)

Maybe the vpn put my clock out of sync? I'm not sure... any help really appreciated.

Cheers,

---

