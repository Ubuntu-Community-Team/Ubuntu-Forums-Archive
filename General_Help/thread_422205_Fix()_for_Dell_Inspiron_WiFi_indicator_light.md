---
title: "Fix(?) for Dell Inspiron WiFi indicator light"
date: 2007-04-24
forum: General Help
---

### Post by jfinkels on 2007-04-24
I think I'm on the right track here...

On my Dell Inspiron 9300 laptop (and apparently on some other Dell Inspiron laptops, see the bug report here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/55780](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/55780) ) the WiFi indicator light fails to turn on and off when I press the enable/disable wireless radio button (although the Bluetooth indicator light works just fine). I used the following command to add "options ipw2200 led=1" to a file at /etc/modprobe/ipw2200.
```

touch /etc/modprobe.d/ipw2200 && echo options ipw2200 led=1 > /etc/modprobe.d/ipw2200

```

The indicator light now turns on along with the Bluetooth indicator light. Unfortunately, disabling the wireless radio fails to turn the indicator light off. Re-enabling wireless radio after disabling it causes the light to turn off for about half a second, then turn right back on.

Does anyone have any ideas for a solution to this problem? This is purely cosmetic; the wireless radio works just fine.

See here for more info on Dell Inspiron 9300 ([https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9300#preview](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9300#preview))

---

