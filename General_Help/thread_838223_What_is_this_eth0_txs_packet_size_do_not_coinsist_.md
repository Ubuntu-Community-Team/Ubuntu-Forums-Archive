---
title: "What is this: eth0: txs packet size do not coinsist with txd...all the time?"
date: 2008-06-23
forum: General Help
---

### Post by hopelessone on 2008-06-23
Hi,

I been trying to find out why all day i get these:

Jun 23 22:43:59 redox-pc kernel: [ 2148.735430] eth0: txs packet size do not coinsist with txd txd_:0x0000003c, txs_:0x000504de!
Jun 23 22:43:59 redox-pc kernel: [ 2148.735433] txd read ptr: 0x1dbc
Jun 23 22:43:59 redox-pc kernel: [ 2148.735434] txs-behind:0x80010183
Jun 23 22:43:59 redox-pc kernel: [ 2148.735435] txs-before:0x000502df
Jun 23 22:43:59 redox-pc kernel: [ 2148.735437] eth0: txs packet size do not coinsist with txd txd_:0x000005ea, txs_:0x00010183!
Jun 23 22:43:59 redox-pc kernel: [ 2148.735438] txd read ptr: 0x1dfc
Jun 23 22:43:59 redox-pc kernel: [ 2148.735439] txs-behind:0x00010036
Jun 23 22:43:59 redox-pc kernel: [ 2148.735440] txs-before:0x000504de
Jun 23 22:43:59 redox-pc kernel: [ 2148.736738] eth0: txs packet size do not coinsist with txd txd_:0x000000a2, txs_:0x000501aa!

Etc....every second every day!...HUGE log files...computer is on 24-7

Anyone got a fix? or suggestion?

Thanks a lot...

---

### Post by pedro_orange on 2008-06-23
I think it's a bug

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/147639](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/147639)

---

