---
title: "Reviving an old netbook"
date: 2012-11-22
forum: General Help
---

### Post by Famicommander on 2012-11-22
I have had an Asus EEE 901 netbook four over three years now and it's been an awesome machine for me, but I feel like the performance of the two built in SSDs (one 4 GB and one 16 GB) has degraded so much that it is getting painful to use. When I got the machine I wasn't aware of TRIM or SSD degradation at all, and since the drives themselves are so old this is what I am betting is going on. It's got a 1.6 ghz Atom and 1 GB of PC 5300, but it's starting to crawl even on Lubuntu. Youtube/Hulu videos take forever to buffer, pages load slowly, etc.

I am already planning to upgrade the RAM to 2 GB tomorrow, but that obviously won't help with the degraded SSDs.

So I intend to try to boot the OS from the internal SD card slot. I was wondering:
1. Would this option on a basic class 10 card be noticeably faster/more responsive than my ancient SSDs?
and
2. Would this old machine be able to take advantage of the new UHS-I SD technology, such as that found in this card:
[http://microcenter.com/product/387642/16GB_Class_10_Secure_Digital_High_Capacity_-_Ultra_High_Speed-I_(SDHC-UHS-I)_Flash_Media_Card_SF16UX-TQ](http://microcenter.com/product/387642/16GB_Class_10_Secure_Digital_High_Capacity_-_Ultra_High_Speed-I_(SDHC-UHS-I)_Flash_Media_Card_SF16UX-TQ)

If I ended up doing both I'd be in for roughly 40 dollars in upgrades, which I think is a reasonable amount to spend in lieu of replacing the whole machine. My goal is to make this machine usable for basic streaming media and browsing, nothing more. Do you think it is a worthy pursuit?

---

### Post by snowpine on 2012-11-22
There's some great info on this site, including tutorials how to replace the SSD:

[http://forum.eeeuser.com/index.php?/forum/55-eee-pc-901-specific-discussion/](http://forum.eeeuser.com/index.php?/forum/55-eee-pc-901-specific-discussion/)

---

### Post by BicyclerBoy on 2012-11-22
I have an old HP atom netbook with the really sloow PATA-SSD but it still runs quite well..(12.04 unity)

Are you sure the drive is not just choked up with old kernel images?

There are some SSD mount options tweaks in /etc/fstab  :
noatime,nodiratime,discard,

I'm only using "noatime", better check out each option one by one..

I have considered adding RAM & replacing the SSD with a fast one but it just seems like a waste of money to me.
The atom & the 945GME chipset is not very good just cheap.

Six months ago the intel drivers & kernel from xorg-edgers made a big difference to video performance.

---

