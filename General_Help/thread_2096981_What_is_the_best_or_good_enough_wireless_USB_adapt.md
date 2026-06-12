---
title: "What is the best or good enough wireless USB adapter to buy?"
date: 2012-12-21
forum: General Help
---

### Post by NicoleCtrl on 2012-12-21
I have a D-Link DWA-125 that is a few years old, that I used to use with Windows.
On Kubuntu 12.10 it is giving me some serious problems, continually disconnecting, sometimes 40-50 times a day and occasionally for several minutes or half an hour. Very frustrating.

Reading up on which wireless USB adapter to buy, I see that with Linux it is kind of a minefield and so I'm curious what works the best or is good enough for a reliable, no-hassle connection?

Alternatively, if anyone knows why D-Link DWA-125 is acting up so much I'd be interested in any fix. What I found so far is very technical, long-winded fixes that don't work half the time anyway. I'm tempted to just buy something new if anyone has a great suggestion. Thanks!

---

### Post by haqking on 2012-12-21
> **NicoleCtrl said:**
> I have a D-Link DWA-125 that is a few years old, that I used to use with Windows.
On Kubuntu 12.10 it is giving me some serious problems, continually disconnecting, sometimes 40-50 times a day and occasionally for several minutes or half an hour. Very frustrating.

Reading up on which wireless USB adapter to buy, I see that with Linux it is kind of a minefield and so I'm curious what works the best or is good enough for a reliable, no-hassle connection?

Alternatively, if anyone knows why D-Link DWA-125 is acting up so much I'd be interested in any fix. What I found so far is very technical, long-winded fixes that don't work half the time anyway. I'm tempted to just buy something new if anyone has a great suggestion. Thanks!

[http://linuxplained.com/linux-compatible-usb-wireless-adapters-2012/](http://linuxplained.com/linux-compatible-usb-wireless-adapters-2012/)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by sudodus on 2012-12-21
I have two Zyxel G-202 USB sticks that work out-of-the box with 12.04 (802.11g - not quite up-to-date). You can find lists browsing the internet to find info and advice about current adapters

for example

[http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html](http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html)
[http://askubuntu.com/questions/173677/wireless-network-adapter-manufacturers-with-best-linux-compatibility-record](http://askubuntu.com/questions/173677/wireless-network-adapter-manufacturers-with-best-linux-compatibility-record)
[http://linuxwireless.org/en/users/Devices/USB](http://linuxwireless.org/en/users/Devices/USB)

---

### Post by kurt18947 on 2012-12-21
I have three N150 adapters that are plug 'n' play.  

1-Netgear WNA1100.  This uses an Atheros chipset and I've found disabling hardware encryption seems to help with throughput on 12.10

2-Dlink DWA-131.  There may be more than one variation of this device.  Here is my lsusb output:[INDENT][INDENT]Bus 003 Device 004: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]
[/INDENT][/INDENT]3-Trendnet TEW-649UB.  This seems to be a twin of the Dlink DWA-131.

There is another choice that is not plug 'n' play but I find it very useful on notebooks.  It's a 'nano' size and only sticks out of the USB port about 1 cm. and seems to have a strong signal.

Edimax ew 7811Un  [http://www.amazon.com/s/ref=nb_sb_ss_i_1_6?url=search-alias%3Daps&field-keywords=edimax%20ew-7811un]("http://www.amazon.com/s/ref=nb_sb_ss_i_1_6?url=search-alias%3Daps&field-keywords=edimax%20ew-7811un")

This adapter will be recognized by Ubuntu 12.xx but will not work well or reliably in my experience.  I download Realtek's driver and extract it.  If you search for my user name in the networking and wireless forum I recently posted a how-to for this adapter.  It may be necessary to blacklist the default rtl-81???? modules in order for the Realtek module to drive the device.  I'm sure there are other excellent choices but these I have experience with.

---

### Post by fredcarru on 2013-02-13
I have a D-link DWA-140 which performed like yours under Ubuntu 11.10. I bought an edimax EW-7811Un which worked fine in the D-link usb extension. When I installed Ubuntu 12.10 neither worked for more than a few minutes. Then I tried using a short usb extension, from a front usb port, and both work. The Edimax is a bit flaky I probably need to use a rear usb port, but the D-link is jut fine..

---

