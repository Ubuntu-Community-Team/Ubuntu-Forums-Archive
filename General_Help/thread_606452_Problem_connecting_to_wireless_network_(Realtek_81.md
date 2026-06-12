---
title: "Problem connecting to wireless network (Realtek 8185)"
date: 2007-11-07
forum: General Help
---

### Post by Purkinje on 2007-11-07
Hello,

I just got 7.10 installed on my machine, and it's working great!....except for my wireless card.  After I enter in the WEP key, it starts to connect, and then suddenly and completely it crashes!  Two of the caps lock buttons are flashing and I have to hard restart.  

Please go slow!  I'm a very uneducated Linux user, and I would love to learn more, but I need you to go slow!

Thanks!

---

### Post by MrFSL on 2007-11-08
It would help if we knew what wireless card you are using.

You can open a terminal and type:
```
lspci | grep -i wireless
```

Just copy the output into a reply message.

---

### Post by Purkinje on 2007-11-08
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

---

### Post by techristian on 2007-11-09
I have the same problem. I have a gateway mx3228 with realtek modem as well.

Dan

*** Advertising removed by staff ***

---

### Post by Purkinje on 2007-11-10
bump.

---

### Post by Purkinje on 2007-11-11
UPDATE:

I tried to connect a different wireless network, which did not use a WEP key, and it worked fine.  So my beginner's opinion of the problem is something to do with the WEP key.  I'm using a 128-bit WEP key, with an Actiontec M1000 Modem.  

Thanks!

---

### Post by MrFSL on 2007-11-12
Sorry, I haven't had a chance to deal with wireless issues in Gutsy yet since I am still clinging to Feisty.

I have had a lot of problems connecting to encrypted networks using the default Network utility supplied by Ubuntu (gnome-network-manager).

You might try using wicd.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

...or some other wireless network connection utility.

---

