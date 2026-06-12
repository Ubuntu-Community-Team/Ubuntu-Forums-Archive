---
title: "How often does the clock gets updated when using Network Time?"
date: 2013-09-28
forum: General Help
---

### Post by vincegata on 2013-09-28
Hi,

I am running Ubuntu 12.04 in fallback mode. I am using Network Time setting for my clock so it synchronizes time off of the internet. However I've noticed that my clock falls behind considerably, about 30 seconds or more in just a couple of days. I develop a program that reads the clock and this lag is no good for me. 

Hence, do you know how often Ubuntu reads the time? Can I change this setting so it updates the clock every hour?

TY

---

### Post by TheFu on 2013-09-28
It doesn't work the same way as on Windows.  NTP learns how much "drift" your system has and predicts it.  The greater the drift, the more often it will check on the network for correct time.  Google "ntp" and read the wikipedia article to learn more than you can stand.

However, if NTP isn't installed, then it will never keep time to the microsecond accuracy we have come to expect. **Do you have NTP installed? **  Also, if outbound UDP is blocked on the network, then your machine probably will not be able to reach time servers.

NTP is one of those things that sorta just works. It isn't like on Windows where sometimes the time settings don't work. I know that I'm not the only person with this issue on Windows (every version since Win95) [http://lifehacker.com/5819797/synchronize-your-windows-clock-with-an-alternative-time-server-to-increase-accuracy](http://lifehacker.com/5819797/synchronize-your-windows-clock-with-an-alternative-time-server-to-increase-accuracy) .

---

### Post by vincegata on 2013-09-29
Thank you for this!

---

