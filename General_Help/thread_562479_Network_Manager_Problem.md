---
title: "Network Manager Problem"
date: 2007-09-28
forum: General Help
---

### Post by cssutto on 2007-09-28
I can not get network manager to work.

I went to /etc/network and commented out all but the lo line.

I have tried it >administration>networking activated and not.

I have read everything I can find on the problem and nothing has helped.

I am running 6.06.

My purpose in getting this up and running is to be able to use WPA-

Any suggestions would be appreciated.

CSSJR

---

### Post by SpiritIsReality on 2007-09-28
howdy

are you dual booting micsoft?
could be this:
see  posts #16,17,26,27 ?
[http://ubuntuforums.org/showthread.php?t=559895&page=2](http://ubuntuforums.org/showthread.php?t=559895&page=2)

trails
edit: I think you should have one more eth or wlan in your /etc/network/interfaces not commented out.

---

### Post by Vadi on 2007-09-28
What card?

Also, an alternative to network manager is wicd ([click]("http://wicd.sourceforge.net/")), and it works for some cards better than NM.

---

### Post by SpiritIsReality on 2007-09-28
Vadi ...thanks for the info.

---

### Post by cssutto on 2007-09-28
description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.

---

### Post by cssutto on 2007-09-28
Vadi:

Thank you!!

I have fooled with that stupid network manager and watched those damn fishes go round and round for days with nothing but frustration.

I tried Wicd on your comment and within 15 minutes, I had my system running wireless and with WPA as well with a KR1 router.

The longest thing about it was to go back to the web site and find that I had to hit Alt-f2 to get it to run.

Now I need to find a way to get it to use my 63 key without my having to enter it every time.

Thanks again.  What a relief.

CSSJR

---

### Post by Vadi on 2007-09-29
You're welcome.

I believe that each network in wicd can have it's own advanced settings, where you can put the key in try poking about there.

---

