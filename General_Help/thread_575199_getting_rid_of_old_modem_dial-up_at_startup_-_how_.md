---
title: "getting rid of old modem dial-up at startup - how please?"
date: 2007-10-13
forum: General Help
---

### Post by smurphs on 2007-10-13
Hi. I've recently moved from my old speedtouch modem to a router, which works much better.

However, on shutting down there's a load of text about attempted dial-up failing.

How do I stop Ubuntu (Feisty) from doing the dial-up on startup? I set it up so long ago I've forgotten what I did! I know there's a startup folder somewhere...

Any pointers much appreciated. The problem with Ubuntu is it's so stable and reliable you don't need to tinker once it's all set up, then you forget everything!! :-) Maybe that's why windows is so unreliable - to keep us all fresh? ;-)

---

### Post by geirha on 2007-10-14
Modem setup should be in /etc/ppp. You probably just need to deactivate the proper scripts in /etc/ppp/ip-up.d and /etc/ppp/ip-down.d. 

I haven't set up any modem, so this is how it looks for me:
```
$ ls /etc/ppp/ip-{up,down}.d
/etc/ppp/ip-down.d:
0000usepeerdns  0dns-down  postfix

/etc/ppp/ip-up.d:
0000usepeerdns  0dns-up  postfix

```

if you have some other scripts than these, deactivate them by removing the execute bit (sudo chmod -x script) or delete them.

---

