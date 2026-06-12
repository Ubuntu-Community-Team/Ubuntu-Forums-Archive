---
title: "[SOLVED] Hotel Wireless"
date: 2008-02-18
forum: General Help
---

### Post by drs305 on 2008-02-18
I'm on a business trip. My gutsy laptop can't connect to the wireless signal although the strength indicates about 60%. It just hangs on acquiring network signal. No password is required until it displays the hotel's home page. 

Wireless worked on the road the last time I tried it (at a different location). I use windows so seldomly to be honest I forgot it was on this machine, but once I remembered and booted to windows I got this internet connection without any problem.

I'd much prefer to use ubuntu. Any suggestions?

Output of iwconfig:
```
no wireless extensions
eth1      no wireless extensions
eth0      IEEE 802.11g  
ESSID:off/any  
Mode:Managed  Frequency:2.462 GHz  
Access Point: Not-Associated   
Bit Rate:54 Mb/s   Tx-Power:32 dBm   
RTS thr:2347 B   Fragment thr:2346 B   
Power Management:off          
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Edit: Not really solved but next day it's working at another hotel.

---

### Post by geraldm on 2008-02-18
What hardware chip is the wireless?
Do the logs show any information on hardware probing, driver messages?  File: /var/log/syslog

Gerald

---

### Post by drs305 on 2008-02-18
It's the 'dreaded' broadcom 43xx but I ndiswrappered it (I think) or whatever I needed to do long ago and it's worked fine in the past. I also have a shortcut on the panel to reset wireless. I'm not on ubuntu at the moment but I think the reset was a sudo modprobe bcmw43xx . I'm getting the signal fine, just won't connect to it.

Thanks for the response. By the way, I'd like someone to teach me about the 'thanks' line. I usually thank people via PM but have noticed there is now a 'thanks' count on posts. Do the moderators do that or should I be doing something to reward people who have helped me out?

---

