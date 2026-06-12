---
title: "iptables, couple questions, please?"
date: 2007-12-18
forum: General Help
---

### Post by posterboy on 2007-12-18
I've learned JUST enough about iptables to be dangerous. :)
I run my own mail server (postfix) and use spamhaus, spamcop and sorbs as additional help to reject spam. Using iptables, i can stop a lot of spam before it ever gets into the computer. A Good Thing. I don't know anyone in Taiwan. There HAS to be a web page where the Class A assignments are listed by country. I googled and googled and found nothing helpful, IANA maybe has this but, I couldn't find it. 
Also, when I use DROP in the iptables rule, what happens to the ratware sending the spam? Does it stall? Do I tie it up for a while? 
TIA

---

### Post by HermanAB on 2007-12-18
Forget about classifying mail by IP address and country - it wont work.

Spamcop and Spamhaus are good.  Add Postgrey, SpamAssassin (with DCC and Razor) and ClamAV to that and be done with it.

Cheers,

Herman

---

### Post by digitalbenji on 2007-12-18
This may or may not be accurate, it is from a webcomic (xkcd)
[http://xkcd.com/195/](http://xkcd.com/195/)

---

### Post by posterboy on 2007-12-18
Thank you!
Really? many years ago, there was a relationship, wasn't there? 
I've got spamassassin running, and I'm very rarely actually seeing a spam come through all these filters. It works, as is. I'm interested in the "play" part of this, and learning a little about iptables. There is NO practical reason, it's just play, and learning.

---

