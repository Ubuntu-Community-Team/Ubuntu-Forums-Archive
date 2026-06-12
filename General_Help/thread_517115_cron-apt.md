---
title: "cron-apt"
date: 2007-08-04
forum: General Help
---

### Post by ant1060 on 2007-08-04
HI,
I have looked for assistance on this, but not found : please forgive if it's somewhere already and I haven't seen it!
I have installed cron-apt to check for daily updates and it runs every night at 4 a.m. (default setting). But when, in the morning, I run sudo apt-get dist-upgrade to install manually, my system seems THEN to start downloading and use the bandwidth - I thought that the downloads happened at 4 in the night and the apt-get dist-upgrade command simply installed them.... What am I doing wrong?
Thanks for help!
Ant

---

### Post by cookfromfrozen on 2007-08-17
i just set up a cronjob with apt-get update && apt-get -y upgrade

-y specifies non interactive mode

works great

---

