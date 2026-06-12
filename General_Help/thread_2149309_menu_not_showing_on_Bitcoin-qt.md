---
title: "menu not showing on Bitcoin-qt"
date: 2013-05-28
forum: General Help
---

### Post by remn on 2013-05-28
I just installed the latest version of Bitcoin-QT on my 12.04 system, and for some reason the menu at the top (i.e. file, settings, etc.) doesn't show when I run the program. I found 2 other threads on this issue but the solutions given haven't gotten the menu to work for me. Here are the links to the other threads:

[http://bitcoin.stackexchange.com/questions/10482/no-menu-in-unbuntu-bitcoin-qt](http://bitcoin.stackexchange.com/questions/10482/no-menu-in-unbuntu-bitcoin-qt)

[https://bitcointalk.org/index.php?topic=187302.0](https://bitcointalk.org/index.php?topic=187302.0)

Any suggestions? I'm thinking about just re-installing ubuntu, maybe upgrading to 13.04. Definitely open to other ideas though.

---

### Post by remn on 2013-05-28
One more thing: When I tried the solution in the second link I posted, the bitcoin program wouldn't open when I clicked on it. So I just reversed the change in the file to get the program to open again.

---

### Post by Francewhoa on 2013-12-07
Confirming this issue with Ubuntu 12.04 LTS

The following worked for me

Run the following command in Terminal
```
 sudo gedit /usr/share/applications/bitcoin-qt.desktop
```

Find the following line
```
Exec=/usr/bin/bitcoin-qt %u
```

under it, add the following line
```
APPMENU_DISPLAY_BOTH=1
```

Close bitcoin-qt, then restart bitcoin-qt

Source: [https://bitcointalk.org/index.php?PHPSESSID=3rkns2nlce516808qh3j67s3q0&topic=187302.msg2994650#msg2994650](https://bitcointalk.org/index.php?PHPSESSID=3rkns2nlce516808qh3j67s3q0&topic=187302.msg2994650#msg2994650)

---

