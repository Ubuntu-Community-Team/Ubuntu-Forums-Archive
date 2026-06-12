---
title: "need sources.list edgy-&gt;current"
date: 2008-05-30
forum: General Help
---

### Post by chunk on 2008-05-30
I never got around to upgrading edgy and now that the edgy repos are down my box is all screwed up.

How can I upgrade without repos? Can anyone give me a good sources.list that I can use to properly upgrade from edgy to current?

Please don't just post any sources.list that works for your system because I don't want to bork my system.

---

### Post by chunk on 2008-05-30
Here's the best I got, but the security updates are still missing for those of us trying to put together a fully updated edgy to minimize upgrade headaches.

```
##### OFFICIAL REPOS #####

## Ubuntu
deb ftp://ftp.heanet.ie/pub/ubuntu/ edgy main restricted universe multiverse
deb-src ftp://ftp.heanet.ie/pub/ubuntu/ edgy main restricted universe multiverse

## Updates
deb ftp://ftp.heanet.ie/pub/ubuntu/ edgy-updates main restricted universe multiverse
deb-src ftp://ftp.heanet.ie/pub/ubuntu/ edgy-updates main restricted universe multiverse

## Backports
deb ftp://ftp.heanet.ie/pub/ubuntu/ edgy-backports main restricted universe multiverse
deb-src ftp://ftp.heanet.ie/pub/ubuntu/ edgy-backports main restricted universe multiverse

```

---

### Post by zvacet on 2008-05-30
In your source list replace **archive.ubuntu.com** with **old-releases.ubuntu.com**

```
sudo apt-get update && sudo apt-get upgrade
```

Better solution is to install Hardy.If you have separate home partition that will not be problem.If you don´t have separate home make one following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.

---

