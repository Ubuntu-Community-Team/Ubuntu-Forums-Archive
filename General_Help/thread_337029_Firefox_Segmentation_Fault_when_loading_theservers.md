---
title: "Firefox Segmentation Fault when loading theserverside.com"
date: 2007-01-12
forum: General Help
---

### Post by dominikroblek on 2007-01-12
Since Firefox has been updated by Ubuntu system update a few days ago if crashes with Segmentation Fault when loading [http://www.theserverside.com](http://www.theserverside.com)

Can I do anything to fix the problem?

---

### Post by dcstar on 2007-01-13
> **dominikroblek said:**
> Since Firefox has been updated by Ubuntu system update a few days ago if crashes with Segmentation Fault when loading [http://www.theserverside.com](http://www.theserverside.com)

Can I do anything to fix the problem?

It loads fine on my system, but then again I'm using Swiftfox: [www.getswiftfox.com](www.getswiftfox.com)

You may want to install one that matches your CPU to see if your Firefox is broken, or if your profile has been corrupted.

---

### Post by mpo on 2007-01-18
> **dominikroblek said:**
> Since Firefox has been updated by Ubuntu system update a few days ago if crashes with Segmentation Fault when loading [http://www.theserverside.com](http://www.theserverside.com)

Can I do anything to fix the problem?

dominik,

I've experienced similar cases with sites on which I had username/passwords remembered by the firefox password-manager.

try removing the password for tss by accessing the 'privacy' section in the firefox preferences.

in my case the problem came back as soon as I let the password-manager store the password again... quite nasty in fact.

-marc=

---

### Post by zanglang on 2007-01-18
Looks fine here... I noticed it has a flash banner on top though. Does flash work on your firefox?

---

### Post by mpo on 2007-01-19
> **zanglang said:**
> Looks fine here... I noticed it has a flash banner on top though. Does flash work on your firefox?

zanglang,

I think this is related to firefox on dapper (not on edgy), and it doesn't have a thing to do with flash AFAICS.

In fact I looked around some more and found the issue is reported here:
  [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77859](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77859)

This IMHO is a serious regression.

Only worrysome part is that apparently the importance is marked 'undecided' yet...

---

