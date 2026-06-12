---
title: "what on earth just happened..."
date: 2007-03-04
forum: General Help
---

### Post by fallscrape on 2007-03-04
Went to bed, all was well

woke up this morning, tried logging into torrentflux remotely, but nothing came up - it was if the machine had been switched off.

I popped up stairs and found that torrentflux wasn't connecting to the database.  Rather than restart mysql I decided to go for a reboot - after all that'd bring everything up and the machine hadn't been down for weeks.

Then a lovely blue screen pops up informing me that x has stopped working.  I have an onboard Nvidia card (from an asus pundit case - for specs see efficientPC on UK ebay)

Gaaaaah.

So I did a quick aptitude update, checked for latest nvidia drivers (there were no new) and restarted x.  Nothing happened.  So I reconfigured x using all the defaults - I just hit escape every time an option came up and it went through the options rather than say, escaping.  Grr.   

But mysteriously x has now started up.  I'm guessing I'm not actually using nvidia drivers now, so how can I dig myself out of this hole.

Also, with insult to injury, I still can't access torrentflux... but that's another matter.

---

### Post by Ramses de Norre on 2007-03-04
There were kernel ugrades a few days ago, you'll need to reinstall the nvidia drivers if you installed these upgrades.

---

### Post by fallscrape on 2007-03-04
> **Ramses de Norre said:**
> There were kernel ugrades a few days ago, you'll need to reinstall the nvidia drivers if you installed these upgrades.

Ahhh... how does one go about doing this?  any linkage?

---

### Post by Ramses de Norre on 2007-03-04
```
sudo aptitude reinstall ...
```
fill in the package names for the drivers.

---

### Post by fallscrape on 2007-03-04
> **Ramses de Norre said:**
> ```
sudo aptitude reinstall ...
```
fill in the package names for the drivers.

Gah wasn't easy but got it running again.  Fingers crossed it don't happen again whilst I'm away!

---

### Post by Ramses de Norre on 2007-03-04
It'll happen on every kernel upgrade... It's an inevitable consequence of installing a new kernel.

---

