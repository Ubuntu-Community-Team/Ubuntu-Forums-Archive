---
title: "64 Studio live CD broke my Kubuntu  :("
date: 2008-03-30
forum: General Help
---

### Post by Dr.Ninethousand on 2008-03-30
I just attempted to run a 64 Studio live CD, it failed to start X, and now Kubuntu won't load up..

well, except in recovery mode..

I noticed booting to recovery, that it got hung up and took a while on something about failing to initialize usb?..

:confused:

---

### Post by Dr.Ninethousand on 2008-03-31
ok that made me think I just wasn't patient enough, so a normal boot did eventually happen, and must have been hung up on the same thing..

and, now none of my USB ports are working - onboard, and my additional PCI card..  :(



edit:

I guess it is seeing my printer, but it won't print..

```

rick@Kutulu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 03f0:2f11 Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000

```

..whoah wait, it just finally printed after like 2 minutes..   :/

---

### Post by Dr.Ninethousand on 2008-03-31
lol, so weird..

apparently all I needed to do was unlplug/replug my bluetooth dongle..   :/

---

