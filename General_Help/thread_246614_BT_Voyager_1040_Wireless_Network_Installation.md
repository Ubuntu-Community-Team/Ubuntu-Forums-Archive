---
title: "BT Voyager 1040 Wireless Network Installation"
date: 2006-08-29
forum: General Help
---

### Post by dragon2309 on 2006-08-29
Hi all, fairly new to linux, ir an Fedora Core a while abck but this if first time in ubuntu. I heard about Dapper Drake 6.06 so downloaded and installed.

I have a BT Voyager 1040 PCI Wireless Card to connect me to ym BT Voyager2100 Wireless Router. Ubuntu does a fairly good job at finding drivers for sound, graphics, input and everything but not for the wireless card.

It identifies the card as a wireless card but assigns it the interface address of eth1, now im a linux n00b but im sure wireless cards whould be given names like wlan0 and wlan1 etc...?? no?

Anyway, thats not the problem. I cant get a connection on the card, i assume due to lack of drivers. I heard about this ndiswrapper thing, i downloaded that, then downloaded the appropriate APPROVED drivers for the Voyager 1040 that are meant to work with ndiswrapper.

So here comes my n00bish-ness, i boot up into unbuntu, open up a terminal, un tar the ndiswrapper (v2.13 if it matters), change directory in the terminal to the newly extracted ndiswrapper directory, then go to perform the MAKE DISTCLEAN and MAKE INSTALL  commands, but both of these report as invalid commands...

And thats where my knowledge stops me im stuck, lol...

Any help guys, ive tried sudo dhclient and everything, i checked that eth1 was actually the wireless card using iwconfig eth1, i even tried setting up the network card amnually by going through all the atributes such as eth1 rate, mode, channel, essid, key etc.....

Please help, im stuck with a brilliant OS but no internet or network connections

cheers all, dragon2309 :D

---

### Post by dragon2309 on 2006-08-29
bump. pleaase help guys

---

### Post by dragon2309 on 2006-08-30
you call this a ubuntu support forum??? wheres the support?

dragon2309

---

### Post by dragon2309 on 2006-08-31
Bump

---

### Post by Blacktalon on 2006-08-31
I don't know to much about that wireless card, I use Broadcom Bluetooth card myself but, if you try looking at [https://wiki.ubuntu.com/WifiDocs/Driver/](https://wiki.ubuntu.com/WifiDocs/Driver/) it might help you out.  And for this type of problem you might wanna try posting it [http://www.ubuntuforums.org/forumdisplay.php?f=139](http://www.ubuntuforums.org/forumdisplay.php?f=139) for better help on the subject.


Good luck to ya!
  ~BT

---

