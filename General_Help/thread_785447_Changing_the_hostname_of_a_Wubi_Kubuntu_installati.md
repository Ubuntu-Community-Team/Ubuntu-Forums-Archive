---
title: "Changing the hostname of a Wubi Kubuntu installation"
date: 2008-05-07
forum: General Help
---

### Post by moglee on 2008-05-07
I want to change the hostname of a Wubi Kubuntu 8.04 installation. I tried changing the name in both hostname and hosts:
127.0.1.1 moglee-xp
However, the moment I do this, KDE dies and is unable to display anything onscreen. So, I also tried in hosts:
127.0.1.1 moglee-xp.xyz.abc.com moglee-xp
But still nothing shows. If I want my system back, I have to boot to command prompt in recovery made and change the hostname to ubuntu and put in the following in hosts:
127.0.1.1 ubuntu.ubuntu-localdomain ubuntu

What am I doing wrong?

---

### Post by ago on 2008-05-07
Can you please ask that in the beginners forum? This forum is dedicated to wubi specific issues. Also, your post might benefit other users interested in the same subject that would be more unlikely to find it in here.

---

### Post by moglee on 2008-05-07
The problem seemed to be a bit Wubi specific -
1. Wubi doesn't ask for hostname during setup
2. Most places where changing hostname is discusses say that changing the name in hosts and hostname file is enough, here its not working.
That is why I thought to try here first :) I'll try asking about this in the beginner's forum also.. Thanks!

---

