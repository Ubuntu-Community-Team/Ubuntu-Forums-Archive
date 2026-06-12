---
title: "Lockups"
date: 2007-10-21
forum: General Help
---

### Post by jmvw on 2007-10-21
Hello,

I have an installation of Ubuntu that normally works great, but under certain conditions the system will lock up. 

My hard drive is a SATA drive connected to a  PPA 2-Port SATA PCI Controller Card that uses the sata_via driver.

The first time my system started locking up is while copying a 120 GB file from a partition on the sata drive to a partition on a new ide drive. It would happen every single time I tried this copy. I did get an error on the console about a soft lockup, but I did not bother to record the precise message.

More recently, I have started to get lockups when running the dvd authoring program QDVDAuthor - not during interactive use, but when building the dvd. When the system locked up, nothing was shown on the console at all.

I suspected the PPA card because this is not very common hardware, so I tried a dd of /dev/sda to /dev/null. No lockup during the entire copy.

My motherboard is an ASUS A7M333

How can I troubleshoot this without error messages on the console?

Thank you,

Michiel

---

### Post by jmvw on 2007-11-08
Heyyy no comments? Did I ask in the wrong place?

Thank you..

---

