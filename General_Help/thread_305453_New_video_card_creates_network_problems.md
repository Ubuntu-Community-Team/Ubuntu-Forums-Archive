---
title: "New video card creates network problems?"
date: 2006-11-23
forum: General Help
---

### Post by Phalangees on 2006-11-23
I had a problem with glxinfo and I came to the conclusion that it was because of my video card so I threw a sort-of old but better then integrated video card in and tried to boot up. The bar got about half way through so then I booted in recovery mode where it stopped at Configuring Network Interfaces. It won't even boot with the live CD with the new card. Without the card my /etc/network/interfaces file looks like this:

>  auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


please someone help.

---

### Post by Phalangees on 2006-11-23
A few other things I forgot to mention.

Something is causing ubuntu to restart all the time. If the screensaver comes on, the computer crashes. I can't change my screen saver because it will crash. There are no progress bars when anything is loading. You can tell where it is because it covers up the text. It's weird. Someone please tell me what to do.

---

