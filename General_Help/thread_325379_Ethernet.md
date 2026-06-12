---
title: "Ethernet"
date: 2006-12-25
forum: General Help
---

### Post by confusimo on 2006-12-25
I have a Duron 600, 256 ram, 160gb hd.  I use the Live CD 32bit 6.06 DD.  Everything works great now.  The CD loads to a desktop and everything.  But the internet doesn't work.  On my main machione 3.06 ghz it works great 64bit 6.06 DD ubuntu.  But I've never tried built-in Ethernet.  That is WIIFI not ethernet so I never tested etherent.

Does Ethernet not work by default on Ubuntu.  Do I need a wifi card on the Duron 600 also.  Or just to test without installing it form the live CD is there a way to enable Ethernet.

Thanks,
Confusimo

---

### Post by jasonlfunk on 2006-12-25
Ethernet should be enabled by default. Make sure you cable is plugged in securely. In the System -> Administration -> Networking you can make sure that your ethernet card is there and is enabled. If you open up a terminal and type 'ifconfig eth0' you can see some settings for the card as well.

---

