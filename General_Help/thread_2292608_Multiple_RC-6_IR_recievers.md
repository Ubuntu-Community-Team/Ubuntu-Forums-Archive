---
title: "Multiple RC-6 IR recievers"
date: 2015-08-29
forum: General Help
---

### Post by speedyrazor on 2015-08-29
Hi, I get the below output when using ```
ir-keytable
```. If I use the IR receiver found at /dev/input/event3 (the first one found) then I get input when using the remote and all works well. But I want to use the IR receiver found at /dev/input/event5 (the second one found), if I use the remote on that IR receiver then I get no response. The reason I have two is the first one (/dev/input/event3) is built into my TBS6984 satellite card, but I don't want to use that IR reciever.
So my question is, how do I use the IR receiver /dev/input/event5 (the second one found)?

```
Found /sys/class/rc/rc0/ (/dev/input/event3) with:
  Driver saa716x, table rc-tbs-nec
  Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
  Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
  Name: saa716x IR (TurboSight TBS 6984)
  bus: 1, vendor/product: 6984:0013, version: 0x0001
  Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc3/ (/dev/input/event5) with:
  Driver mceusb, table rc-rc6-mce
  Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
  Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
  Name: Media Center Ed. eHome Infrared 
  bus: 3, vendor/product: 147a:e017, version: 0x0140
  Repeat delay = 500 ms, repeat period = 125 ms

```

Kind regards.

---

