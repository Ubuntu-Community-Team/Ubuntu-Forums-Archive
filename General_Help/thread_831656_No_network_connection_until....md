---
title: "No network connection until..."
date: 2008-06-17
forum: General Help
---

### Post by maybevader on 2008-06-17
I'm running the latest version of Ubuntu (8.04), and have some problems with the network connection. It seems that every time I boot up the computer i have to run sudo ifdown wlan0 / sudo ifup wlan0 before i get a connection. I am very new to this, and I only have been using Linux for 3 days. Don't even know if I have to run both those commands in order to get online. 

I'm running win xp and ubuntu in a dual boot, and every time I boot up windows i'm online without doing anything.

Sorry if this isn't enough info. I searched the forum but couldn't find a similar problem.

Help plz? :confused:

---

### Post by plucky on 2008-06-17
> **maybevader said:**
> I'm running the latest version of Ubuntu (8.04), and have some problems with the network connection. It seems that every time I boot up the computer i have to run sudo ifdown wlan0 / sudo ifup wlan0 before i get a connection. I am very new to this, and I only have been using Linux for 3 days. Don't even know if I have to run both those commands in order to get online. 

I'm running win xp and ubuntu in a dual boot, and every time I boot up windows i'm online without doing anything.

Sorry if this isn't enough info. I searched the forum but couldn't find a similar problem.

Help plz? :confused:


The problem might be your system is looking at your wired connection instead of the wireless.
Left click in the icon that looks like two monitors and select manual configuration.

Click on unlock and enter login password.

Make sure wired connection is unticked and wireless is ticked.

Hopefully that should now work.


If not post output of ```
ifconfig
iwconfig
lspci
```


Good Luck

---

### Post by maybevader on 2008-06-17
It works now. Thank you :)

---

