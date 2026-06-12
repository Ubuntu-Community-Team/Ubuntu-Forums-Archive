---
title: "Why has my computer become slow since about a month"
date: 2020-01-26
forum: General Help
---

### Post by aneblanc on 2020-01-26
I am trying to understand why my wife's laptop has become very slow since about a month while mine has no problems. 
We have approximatively the same laptops (hers is a 14", mine is an 11") bought at about the same time with the same configurations HP Stream with  Intel® Celeron(R) CPU N3060 @ 1.60GHz × 2 processor, 4GB RAM, 64bit, 26.5GB disk + 32GB HD drive, Chromium Version 79.0.3945.79 (Official Build) Built on Ubuntu, running on Ubuntu 16.04 (64-bit).
What kind of tests can I run to find out the problem?

---

### Post by dragonfly41 on 2020-01-26
Not guaranteed to fix your problem but I frequently refer to Stacer dashboard.
Download from here ..

[https://github.com/oguzhaninan/Stacer](https://github.com/oguzhaninan/Stacer)

Being an Electron app it does consume some resources compared with command line operations but it has most tools under one roof.
Look at Services and Processes reports.

---

### Post by aneblanc on 2020-01-27
It seems that chromium is slowing down the laptop as the problem does not appear with firefox. 
Where could the problem with chromium be and how could I fix it?

---

### Post by dragonfly41 on 2020-01-27
Start by disabling extensions, test performance, then enable extensions one by one until you hit problems.
Install an extension such as Session Buddy to save multiple tabs.

---

### Post by aneblanc on 2020-01-30
It seems that chromium is slowing down the laptop as the problem does not appear with firefox. 
Where could the problem with chromium be and how could I fix it?
I only have adblock as extensions.

---

### Post by physics2014 on 2020-01-30
I am in no way an expert but knowing this helped me the previous time. 
Some times it is a sign of a hard-disk that is about to fail or the connector from hard-disk to the motherboard that is about to fail. It happened to my previous PC. If you have the chance try to remove the hard-disk and try to boot it on another computer, if it works properly than it [SIZE=3]**could**[/SIZE] be sign of the connector failing, otherwise it could be the Hard-Disk about to fail.

---

### Post by dragonfly41 on 2020-01-30
> [COLOR=#000000]Where could the problem with chromium be and how could I fix it?[/COLOR]

Assuming that you now have Stacer installed as suggested earlier look at the  Processes view and search chromium (so that you only view chromium processes).

There are a number of core processes without tabs, and each tab adds another running process.

Inspect CPU usage and Memory usage per process. Compare profiles across your two laptops.

In Stacer > System Cleaner you can inspect Application Caches and see size of Chromium cache.

---

### Post by NM5TF on 2020-01-30
> **aneblanc said:**
> It seems that chromium is slowing down the laptop as the problem does not appear with firefox. 
Where could the problem with chromium be and how could I fix it?
I only have adblock as extensions.

Chromium is Google based, so it is sending all your browsing back to Google for sale to the highest bidder...that coupled
with AdBlock makes it even slower....I have the same problems at some sites even with Firefox & AdBlock running...there
is a new browser lately called Brave that I have heard some good things about, but have not personally tried yet....

if you pause/disable AdBlock does it speed up again ???...

---

### Post by jdeca57 on 2020-01-30
> **aneblanc said:**
> I am trying to understand why my wife's laptop has become very slow since about a month while mine has no problems. 
We have approximatively the same laptops (hers is a 14", mine is an 11") bought at about the same time with the same configurations HP Stream with  Intel® Celeron(R) CPU N3060 @ 1.60GHz × 2 processor, 4GB RAM, 64bit, 26.5GB disk + 32GB HD drive, Chromium Version 79.0.3945.79 (Official Build) Built on Ubuntu, running on Ubuntu 16.04 (64-bit).
What kind of tests can I run to find out the problem?

The same hardware/software  and different experience? Look at disk space. Maybe a partition is (nearly) full. Don't install extra software, that won't help.

---

