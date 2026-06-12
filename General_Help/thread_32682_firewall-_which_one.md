---
title: "firewall- which one?"
date: 2005-05-09
forum: General Help
---

### Post by [pl]ice on 2005-05-09
hi, i'm after a firewall :/

best if it's a daemon, not X supported(or both) wich can log all data,eg time stamp, no. of hits to a port, protocol, etc.
i have tried some gui's but i don't like it, eg. firestarter, nice but won't give out enough info, 
anyway i would like to run ubuntu without X, so yeh,
and a, not too much complicated .....  :)

any ideas?

thanks!!!!

---

### Post by mohaham on 2005-05-09
Have you tried GuardDog firewall..
It can be run as a daemon..

---

### Post by Dax0r on 2005-05-09
Firestarter(add backports for the current version),but u cant set Tcp or Udp protocol

---

### Post by [pl]ice on 2005-05-09
um, but firestarter won't run outside X ....

i'll check up guarddog, i've tried to use ip-cop, but there were some problems, maybe will give it a go again :)
thnx

---

### Post by iNs4ne on 2005-05-11
[QUOTE='[pl]ice']um, but firestarter won't run outside X ....

i'll check up guarddog, i've tried to use ip-cop, but there were some problems, maybe will give it a go again :)
thnx[/QUOTE]

errm... Firestarter runs outside X, just not the pretty GUI  ;-)

---

### Post by hashimoto on 2005-05-12
Firestarter runs as a daemon on the background. I won't get killed when you close the GUI.

---

### Post by JonahRowley on 2005-05-12
If you want to get really serious, use iptables for your actual firewall.  Since it sounds like what you really want is an IDS, use Snort for alerting.  This is probably not what you're looking for since it sounds like you want something that's reasonably easy to run, but it would be the "best" solution.

iptables itself can do quite a bit, including logging.  Depending on what you want, iptables might be what you're looking for.  For more info on iptables, see [http://www.netfilter.org](http://www.netfilter.org)

---

