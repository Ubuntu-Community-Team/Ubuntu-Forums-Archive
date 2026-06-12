---
title: "How safe is it to use ppa:gwendal-lebihan-dev/cinnamon-stable?"
date: 2013-10-28
forum: General Help
---

### Post by Vannyi on 2013-10-28
A Google search shows that I can install Cinnamon on my Ubuntu 12.04 machine using the PPA sudo apt-add-repository ppa:gwendal-lebihan-dev/cinnamon-stable

I'm just wondering how do we tell who maintains this PPA?  Is it something put out by the official Linux Mint team or was it created by a Linux Mint user?

Thank you

---

### Post by deadflowr on 2013-10-28
The ppa is totally safe.
However, it should be noted that the version in stable breaks unity in 13.10( at this time).
I don't know what happens with 12.04.
If you don't use unity, you should be fine.
As precaution, you should install ppa-purge.
[http://www.theorangenotebook.com/2012/01/ppa-purge-magic-undo-buttton.html](http://www.theorangenotebook.com/2012/01/ppa-purge-magic-undo-buttton.html)

---

### Post by Vannyi on 2013-10-29
> **deadflowr said:**
> The ppa is totally safe.

Thank you for confirming.

For my own understanding, could you tell me, is this PPA maintained by the Linux Mint developers for Ubuntu users or was it created by someone from the "community" to port Cinnamon over to Ubuntu?  I've tried to Google this and can't seem to find any information.

---

### Post by vasa1 on 2013-10-29
> **Vannyi said:**
> Thank you for confirming.

For my own understanding, could you tell me, is this PPA maintained by the Linux Mint developers for Ubuntu users or was it created by someone from the "community" to port Cinnamon over to Ubuntu?  I've tried to Google this and can't seem to find any information.

Get a Launchpad account and then visit this: [https://launchpad.net/~gwendal-lebihan-dev](https://launchpad.net/~gwendal-lebihan-dev)

---

### Post by deadflowr on 2013-10-29
Yeah, it's hard to figure out what the ppa's maintainers status is, but the ppa is the supported method to install it on Ubuntu from the mint site.
[http://cinnamon.linuxmint.com/?page_id=61](http://cinnamon.linuxmint.com/?page_id=61)

---

### Post by Vannyi on 2013-10-29
> **deadflowr said:**
> Yeah, it's hard to figure out what the ppa's maintainers status is, but the ppa is the supported method to install it on Ubuntu from the mint site.
[http://cinnamon.linuxmint.com/?page_id=61](http://cinnamon.linuxmint.com/?page_id=61)

More for interest, would you happen to know, is this the same PPA that is used when you try and install Cinnamon on one of the later editions of Ubuntu through the Software Center?

---

### Post by deadflowr on 2013-10-29
> **Vannyi said:**
> More for interest, would you happen to know, is this the same PPA that is used when you try and install Cinnamon on one of the later editions of Ubuntu through the Software Center?

No.
The version in the repos is frozen.
And typically, the one in the repos is assigned to be maintain by an Ubuntu Developer.
Though the one in the repos is frozen(at 1.74) it will still get whatever security fixes that come down for it, if any.

The ppa will roll on and update to newer and newer versions as soon as it hits what is considered stable.
So now it's at version 2.0(something) and at some point it will be at 2.1. If you keep your system update and don't disable the ppa, you'll roll into that next version when it comes.

---

### Post by Vannyi on 2013-10-29
> **deadflowr said:**
> No.
The version in the repos is frozen.
And typically, the one in the repos is assigned to be maintain by an Ubuntu Developer.
Though the one in the repos is frozen(at 1.74) it will still get whatever security fixes that come down for it, if any.

The ppa will roll on and update to newer and newer versions as soon as it hits what is considered stable.
So now it's at version 2.0(something) and at some point it will be at 2.1. If you keep your system update and don't disable the ppa, you'll roll into that next version when it comes.

Would you have by chance have come across any reading that might have explained the developers rationale for not having Cinnamon in the Software Center for Ubuntu 12.04 as it is there for later versions?

---

### Post by deadflowr on 2013-10-29
The most likely scenario for cinnamon not ending up in the release of precise would be because it hadn't reach the level of testing by the Ubuntu community to get itself into the release cycle in time for the freeze.

---

### Post by Vannyi on 2013-10-30
> **deadflowr said:**
> The most likely scenario for cinnamon not ending up in the release of precise would be because it hadn't reach the level of testing by the Ubuntu community to get itself into the release cycle in time for the freeze.

Does that mean that once a release version (eg 12.04, 13.04, 13.10) is made available to the public, there will be no additions/deletions to the software center and that the only way to get newer software packages is by upgrading your version of Ubuntu?

Thank you

---

### Post by CaptainMark on 2013-10-30
deadflowr is correct about why Cinnamon is not in 12.04 standard repos, at the time of release there was no-one available to re-package Cinnamon for Ubuntu because the Mint devs were working hard building cinnamon and no-one from Canonical was interested in doing it.
As for the status of the PPA, Gwendal is on the Mint development team so it is an official release channel not a community effort, (source: I asked him the same question a few years ago)

There you go, something more reliable [https://github.com/linuxmint?tab=members](https://github.com/linuxmint?tab=members)

---

### Post by deadflowr on 2013-10-30
> [COLOR=#000000]Canonical was interested in doing it.[/COLOR]

I think they're still not interested in doing it.
Thanks for digging up the link on the mint devs.

---

