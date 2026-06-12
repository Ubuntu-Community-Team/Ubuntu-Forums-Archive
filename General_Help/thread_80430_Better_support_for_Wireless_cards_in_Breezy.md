---
title: "Better support for Wireless cards in Breezy?"
date: 2005-10-22
forum: General Help
---

### Post by David vs. Goliath on 2005-10-22
Does Breezy have better support for Wireless cards?

If it is worth it to install it......

I have tried Hoary with ndiswrapper but it dosent work.


I have an Laptop Fujitsu Siemens Amilo D with an D-link DWL-610 card.

Any body who got it to work with this card?


Note that my english is not so good :)

---

### Post by Psquared on 2005-10-22
I'd say the support is about the same. My only experience is with my Intel Pro Wireless (built-in) and it took days of tweaking and hacking different ideas to finally get it to work. So far it has stayed up for 36 hours without flaking out.

Ndiswrapper seems too complex and I don't like the idea of hacking Linux with a m$ driver. Something about it rubs me the wrong way.:rolleyes: 

Anyway, some of these cards work straight away and some require hacking. I'd do a search of your particular card and see what the success rate is. It might be fine.

BTW, Breezy has other improvements (under the hood) which make the upgrade worthwhile.

---

### Post by shenki on 2005-10-22
dont let ndiswrapper put you off, it's as simple as running one command to install the windows driver, and then doing a 'modprobe ndiswrapper' when you want to bring the wireless interface up.

```
sudo ndiswrapper -i <windows driver>.inf
sudo modprobe ndiswrappwer
```

for your dlink card, have a look at [http://ubuntuforums.org/showthread.php?t=26751](http://ubuntuforums.org/showthread.php?t=26751), it looks like all you need to do is use ndiswrapper - [https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper) - to load the windows driver.

As with most things, you will find more support for hardware in later releases, so go for the upgrade.

---

### Post by David vs. Goliath on 2005-10-22
[QUOTE=shenki]dont let ndiswrapper put you off, it's as simple as running one command to install the windows driver, and then doing a 'modprobe ndiswrapper' when you want to bring the wireless interface up.

```
sudo ndiswrapper -i <windows driver>.inf
sudo modprobe ndiswrappwer
```

for your dlink card, have a look at [http://ubuntuforums.org/showthread.php?t=26751](http://ubuntuforums.org/showthread.php?t=26751), it looks like all you need to do is use ndiswrapper - [https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper) - to load the windows driver.

As with most things, you will find more support for hardware in later releases, so go for the upgrade.[/QUOTE]

Ok...I might give it another try........Thx

---

### Post by nomuna on 2005-12-20
I have the same card as yours. I am using it under Hoary. Downloaded the 
driver for rtl8180 chipset and did what was written in the Wiki about rtl8180 cards and it worked. No ndiswrapper. I am using the card at the University with ipsec and wep etc. It is a bit slow sometimes.

Under Breezy and Fedora 4 I couldn't compile the driver.  I would say use Hoary. The rtl8180 project seems to be on ice. I have been visiting the website of the project at least a week to see if a new version compatible 
with gcc4 and Kernel 2.6.11 came out. But nothin' so far...

---

### Post by Mr. Electric Wizard on 2005-12-20
I for one think that ndiswrapper is perfectly ok.
this was about the only option for my broadcom based wifi card...
good luck.  There are several great HOWTO's on this site to get you up and running...

---

