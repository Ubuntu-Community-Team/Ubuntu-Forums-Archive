---
title: "Downgrading"
date: 2020-03-10
forum: General Help
---

### Post by alcapucino on 2020-03-10
Howdy, any one knows if possible to downgrade Ubuntu 18.04.4 LTS to Ubuntu 16?
Also is Ubuntu 16 available for downloading any more?
Thanks

---

### Post by CelticWarrior on 2020-03-10
> **alcapucino said:**
> Howdy, any one knows if possible to downgrade Ubuntu 18.04.4 LTS to Ubuntu 16?
Also is Ubuntu 16 available for downloading any more?
Thanks

No, it isn't. 
If you want 16.04, install 16.04. A mistake, obviously, because it has only about one year left of support and really there's no point in using old releases.
Better to post about the problem you're trying to solve.

---

### Post by guiverc on 2020-03-10
Ubuntu Core 16 is an IoT release of Ubuntu (releases that rely heavily on snaps use *yy* format) and it's not the same as a server/desktop release (which uses *yy.mm* format) even if based on them. 

Flavors of 16.04 are already EOL, however Ubuntu 16.04 LTS with Unity 7 desktop, Ubuntu 16.04 Server (no desktop) or Ubuntu 16.04 Kylin still have months of support left. Yes you can still download them, they'll have ~9 months of supported life left though with most 16.04 'universe' packages no longer being maintained (five years of support applies to 'main' largely) consider that first.

Automatic tools upgrade to later packages, doing it in reverse is more manual.

---

### Post by HermanAB on 2020-03-10
It may be better to make a virtual machine using the old version, rather than downgrading the host.

---

### Post by TheFu on 2020-03-10
> **alcapucino said:**
> Howdy, any one knows if possible to downgrade Ubuntu 18.04.4 LTS to Ubuntu 16?
Also is Ubuntu 16 available for downloading any more?
Thanks

There's a big difference between what might be possible and what is tested, or a good idea.

Going from 18.04 --> 16.04 is not a good idea and it is not tested. But if you do manual stuff, you might be able to use your personal expertise to make it happen.  It won't be automatic and will be extremely manually for every package.  In the end, you'd be better doing a fresh 16.04 install and feeding in a list of specific packages, sans version numbers, to the package manager for installation.

While no-hassle, free support ends for 16.04 in about a year, there is full-of-hassle support available after that.  In a business environment, paying makes the most sense.  For home users, with 1-2 systems, there is a free extended support option at the cost of your privacy.  There was an announcement about this for the 14.04 release.  
[https://www.omgubuntu.co.uk/2018/09/ubuntu-14-04-extended-security-maintenance-esm](https://www.omgubuntu.co.uk/2018/09/ubuntu-14-04-extended-security-maintenance-esm)

---

