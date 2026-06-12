---
title: "Can't Connect Firefox 24 to Office365.com"
date: 2013-10-22
forum: General Help
---

### Post by neodaemon on 2013-10-22
Two PC's:  System76 Bonx7 (Ubuntu 13.10 x64)  <and>  a clone desktop (Ubuntu 12.04 x64)
Both run Firefox v. 24.0

From both computers, in Firefox (also tried with Chrome) - I cannot connect/log into  outlook.office365.com  -which is how I check my personal email.

I have a third computer, running Linux Mint 14 KDE, and same Firefox version. This computer connects to outlook.office365.com without a problem.

All computers are right next to each other, on the same gigabit switch, behind the same hardware firewall/router appliance.

I've rebooted, double-checked security settings, DNS, name resolution, etc. I've scoured these forums and Google for ideas - nothing. This is a recent development, though I can't be sure when exactly it started.

Any help or insight would be greatly appreciated.

---

### Post by neodaemon on 2013-10-27
No ideas?   Running from a Live CD of Ubuntu 12.04 or 13.10 produce the same results; web browsing anywhere - even with heavy flash integration is fine - BUT NOT Office365.com. For some reason that site just won't connect - I get the dreaded "Server not found". But on the same machine, booting from a Mint with Cinnamon Live CD, no problem. I really would prefer to stay with the Ubuntu original, and  _not_  have to migrate my work email off of the Office365.com platform.

---

### Post by mastablasta on 2013-10-28
maybe somethign to do with ipv4 or ipv6 settings?

i have same issue on windows XP maschine. the only one that can't connect to libre office website. server not found... i am not sure what is going on lately.

---

### Post by neodaemon on 2013-10-28
Ok, so I started all over again with troubleshooting. Every time I installed any version of Ubuntu (12.x 13.x) I had the same problem - cannot connect to Office365.com. It takes 10+ minutes to timeout, then I get "Server not found". I can install Linux Mint, or Windows 7 on the same machine and then connect without a problem. I use DHCP on my home network, all clients get the same DNS servers, which are my ISP. On a hunch I tried statically assigning the DNS servers from another pair supplied by my work ISP. Bingo - connected right up. Then I statically assigned my home ISP DNS servers again - cannot connect. It appears so far, the only website affected by my ISP DNS is Office365.com. Unbelievable. So if anyone has a strange issue like this - try changing their ISP.

---

