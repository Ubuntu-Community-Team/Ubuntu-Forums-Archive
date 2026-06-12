---
title: "Bittorrent being slow?"
date: 2006-11-04
forum: General Help
---

### Post by kishe on 2006-11-04
I've tried Azureus, Bittornado, Deluge, Ktorrent...I've turned NAT off, I've tried everything...yet best I can do regardless of torrent is 20kb down 75kb up...on a 8/1 ADSL...

Cookie to anyone that can help me solve this :)

---

### Post by matt_risi on 2006-11-04
Same issue, I get TERRIBLE torrent speeds at best. Using ADSL.

---

### Post by zek725 on 2006-11-05
Port settings already set? NAT firewall configured? Seeds? Peers?

---

### Post by ser1alsn1per on 2006-11-05
alrite mate I HAD the same problem I used ports 43029 tcp/udp set that in azureus and turned upnp OFF    and mine was fliying


hope it helps

---

### Post by Unknowndeepness on 2006-11-05
I had this problem once, it helped by removing IPV6..

( edit /etc/modprobe.d/blacklist, add a line that sais "blacklist ipv6", reboot )

Worth a try, dont you think? :)

---

### Post by blacha on 2006-11-05
How ipv6 could have been a slow down there ?
And beyond NAT port problems, ul/dl ratio is also a case. So don't lower your upload too much because it can affect your download speed.

btw. try qBittorent, it's light, fast and looks nice.

---

### Post by zek725 on 2006-11-05
[http://www.bittornado.com/faq.html](http://www.bittornado.com/faq.html)

> You may be flooding your connection. Reduce your upload to 90% of your total upstream bandwidth.

---

