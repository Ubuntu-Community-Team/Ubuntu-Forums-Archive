---
title: "Pidgin issue with MSN protocol on Ubuntu"
date: 2014-12-30
forum: General Help
---

### Post by ric_Poirier on 2014-12-30
Hi,

For several weeks now, I have been unable to log into my MSN account via Pidgin. One day I just hit the pidgin Icon, as usual, and I got the following error message:

[CENTER]**address@live.com disconnected.** Connection error from Notification server. Connection refused.

[/CENTER]
Here is what appears in the Debug Window:

```

[COLOR=#000000]01:01:03) **account:** Connecting to account adress@live.com.
(01:01:03) **connection:** Connecting. gc = 0x7ffee05e3150
(01:01:03) **msn:** new httpconn (0x7ffee0593260)
(01:01:03) **dnsquery:** Performing DNS lookup for gateway.messenger.hotmail.com
[/COLOR][COLOR=#666666](01:01:03) **msn:** C: NS 000: VER 1 MSNP18 CVR0
[/COLOR][COLOR=#660000](01:01:03) **dns:** DNS child 9813 no longer exists
[/COLOR][COLOR=#000000](01:01:03) **dns:** Created new DNS child 9832, there are now 1 children.
(01:01:03) **dns:** Successfully sent DNS request to child 9832
(01:01:03) **dns:** Got response for 'gateway.messenger.hotmail.com'
(01:01:03) **dnsquery:** IP resolved for gateway.messenger.hotmail.com
(01:01:03) **proxy:** Attempting connection to 157.56.108.81
(01:01:03) **proxy:** Connecting to gateway.messenger.hotmail.com:80 with no proxy
(01:01:03) **proxy:** Connection in progress
(01:01:03) **proxy:** Connecting to gateway.messenger.hotmail.com:80.
[/COLOR][COLOR=#FF0000](01:01:03) **proxy:** Error connecting to gateway.messenger.hotmail.com:80 (Connection refused).
(01:01:03) **proxy:** Connection attempt failed: Connection refused
(01:01:03) **msn:** HTTP: Connection error: Connection refused
(01:01:03) **msn:** Connection error from Notification server (gateway.messenger.hotmail.com): Connection refused
[/COLOR][COLOR=#666666](01:01:03) **msn:** C: NS 000: OUT
[/COLOR][COLOR=#000000](01:01:03) **connection:** Connection error on 0x7ffee05e3150 (reason: 0 description: Connection error from Notification server:
Connection refused)
(01:01:03) **account:** Disconnecting account adress@live.com (0x7ffedfc39160)
(01:01:03) **connection:** Disconnecting connection 0x7ffee05e3150
(01:01:03) **msn:** destroy the OIM 0x7ffedfea3220
(01:01:03) **msn:** destroy httpconn (0x7ffee0593260)
(01:01:03) **connection:** Destroying connection 0x7ffee05e3150[/COLOR]

```

I must admit I don't really understand what the problem is. Also, I don't understand what caused this, as I did not change any of the settings for my account.

Thanks,

---

### Post by bashiergui on 2014-12-30
MSN shut down its messenger service on October 31. They want you to use Skype instead.
[http://www.forbes.com/sites/amitchowdhry/2014/08/31/msn-messenger-is-completely-shutting-down-on-october-31st/](http://www.forbes.com/sites/amitchowdhry/2014/08/31/msn-messenger-is-completely-shutting-down-on-october-31st/)

---

### Post by ric_Poirier on 2015-01-03
Ah! Thanks...

---

