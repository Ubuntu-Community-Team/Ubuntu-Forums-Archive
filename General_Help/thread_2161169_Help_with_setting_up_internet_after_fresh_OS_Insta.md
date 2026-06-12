---
title: "Help with setting up internet after fresh OS Installation."
date: 2013-07-09
forum: General Help
---

### Post by Adrenochrom3 on 2013-07-09
okay so i just installed Ubuntu 9.10 which is my favorite version so far. but i installed it, and i cant get any type of internet connection. i figured a hardwire via ethernet cord straight to the modem would give me internet, and it didnt. so my computers ethernet port i guess isnt on, or doesnt have a driver or what. someone please help!

---

### Post by sefs on 2013-07-09
what does a 

```

ifconfig

```

show?

---

### Post by sanderj on 2013-07-09
> **Adrenochrom3 said:**
> okay so i just installed Ubuntu 9.10 which is my favorite version so far. 

Interesting, but 9.10 is not supported anymore. See [https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

You can install it on old hardware, but it possibly won't work on hardware released after 2009-10.

EDIT:
You could find a pre-2009 ethernet card and install that.

---

### Post by Adrenochrom3 on 2013-07-09
Ifconfig:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

This is weird tho because isnt it supposed to have like 2 other things on there for like the network and the ethernet ports? (I dont have it connected to the modem)

---

### Post by tareqjhe1 on 2013-07-09
See carefully and setup your setting.

---

### Post by grahammechanical on 2013-07-09
ifconfig should list your ethernet ports as eth0 and eth1, if you have two and a wieless adapter as wlan0. It could be, as has been suggested, that the Linux kernel in Ubuntu 9:10 does not have firmware for the ethernet and wireless adapters in your machine.

Regards.

---

### Post by Adrenochrom3 on 2013-07-09
This is what came up when I typed > lspci -nn < into terminal


lspci -nn:

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0106] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Device [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Device [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:1c10] (rev b4)
00:1c.5 PCI bridge [0604]: Intel Corporation Device [8086:1c1a] (rev b4)
00:1c.6 PCI bridge [0604]: Intel Corporation Device [8086:1c1c] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation Device [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Device [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Device [8086:1c22] (rev 04)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
03:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:2062] (rev c1)

---

### Post by wildmanne39 on 2013-07-09
Hi, my research shows that there is a bug for your ehternet card in 9.10 but works perfect in 12.04.2, since you can not get any updates including security updates for 9.10 I recommend you upgrade.

Your wireless card could be made to work in 9.10 but you need an internet connection to install it.
Thanks

---

### Post by Adrenochrom3 on 2013-07-09
well ismt there a way i can download the patch for my ethernet card on this computer and transfer the file to my laptop via flash drive, then manually install the driver? i just dont know what file im supposed to download to install. can anyone help with that please?

---

### Post by BreezyBrooke on 2013-07-09
Ubuntu 9.04 is End Of Life and isn't supported. Yea, you may love the Gnome/GTK2 desktop, but you are just beating a half-rotten, dead horse. Please, upgrade to 12.04. and if you want a Gnome/GTK2 like desktop, install gnome-session-fallback which gives you the classic Gnome 2 interface.

---

### Post by Adrenochrom3 on 2013-07-09
uhg i didnt want to have to upgrade. i was just hoping someone would be nice enough to help me get 9.10 working.

---

### Post by wildmanne39 on 2013-07-09
It is not a matter of being nice enough, it is a matter of it is more then one file, many packages for dependencies have to be installed which is hard because they no longer exist in the regular repositories but also because you do not have an internet connection to install them if they did.

I looked but did not find a way for you to do it in 9.10.

You would be hacked because of the security issues created by using an old version that does not get updates anymore.

---

