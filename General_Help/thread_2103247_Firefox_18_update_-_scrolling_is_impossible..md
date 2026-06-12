---
title: "Firefox 18 update - scrolling is impossible."
date: 2013-01-09
forum: General Help
---

### Post by ajgreeny on 2013-01-09
I have just this minute updated my 10.04 installation with the latest versions of Firefox 18 and Thunderbird 17.0.2.

Thunderbird is still fine but scrolling any pages in FF 18 is totally impossible, going nowhere, and stuttering up and down several seconds after using the mouse wheel.  This was occurring in all web pages, not just this forum, which I admit is not good even in FF 17, though it is still usable.

In order to get Firefox usable again I have removed FF and downgraded back to FF 17.0.1 by using the packages in /var/cache/apt/archives.  Has anyone else seen any degradation of scrolling that has come with this FF update, or is it simply my hardware/software incompatibility problem with this version?

EDIT:
Sempron 2400+, 2GB ram, ATI 9200SE graphic card running radeon open source driver.

PS:
I'm just about to update my Xubuntu 12.04 on this same machine to see if it is related to Ubuntu 10.04 on this hardware, or a general FF 18 problem with the hardware.

I will report back.

EDIT 2:
I have just updated my Xubuntu 12.04 on the same machine and FF 18 is also unusable in that and therefore now downgraded as well.  I shall wait until the next version arrives and try that.
However on my old laptop with a celeron 2.66GHz, 512 MB ram and ATI Mobility radeon 9000, everything runs OK, so it must be the particular hardware on the one machine that causes the problem.

EDIT 3:
Same problem in Xubuntu 12.10 on this machine with FF 18, so all points to a particular hardware problem.

---

### Post by tgalati4 on 2013-01-09
Does it make a difference if you have smooth scrolling turned on or off in preferences?

Try running firefox from a terminal so that you can see error messages in the terminal.  Post any of interest.

---

### Post by ajgreeny on 2013-01-10
I have tried FF 18 again and I am still no further forward. Turning off smooth-scrolling and autoscroll in FF preferences makes no difference, and the only error I see if I start in terminal is ```
ATTENTION: default value of option force_s3tc_enable overridden by environment.
```a problem I asked about in [http://ubuntuforums.org/showthread.php?t=2074824](http://ubuntuforums.org/showthread.php?t=2074824) and thought was solved by an upgrade of FF, but has now reappeared.

So now I'm back with FF 17.0.1 which is much better, but I'm aware of possible security risks sticking with an older version.  I still think this must be related to my hardware combination, probably the ATI 9200SE card.

---

