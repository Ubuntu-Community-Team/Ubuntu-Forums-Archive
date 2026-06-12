---
title: "thanks for your help!"
date: 2013-04-06
forum: General Help
---

### Post by eyeneedhelp on 2013-04-06
i am a long way from really knowing what i'm doing!, but i now routinely use my ubuntu machine and while its hard to describe exactly the differences, i find it much more useable than (windows7)or even xp.
one mechanical thing i run into,(could be my comp hdwe), is the keyboard sometime does not work, the 3 leds on the right flash with each keystroke till i unplug it and replug in?

also sometime the password request ignores keystrokes and/or repeats a few times till it decides to read and respond?

otherwise i am making progress and i love the boot time beating my w7 lap by MINUTES!!
i have trouble with terminology but i find a lot of little things that seem more "sensible" than w7 and ill try to get specific in the future fwiw.

---

### Post by Frogs Hair on 2013-04-06
If Ubuntu is on a desktop and you have another keyboard swap it to find out if it is the hardware/driver or software. If you type the password correct except for one character there can be a delay before it offers a try again option, but.  it seems more a keyboard issue. 

Ubuntu Terms: [https://help.ubuntu.com/community/Glossary](https://help.ubuntu.com/community/Glossary)

---

### Post by tgalati4 on 2013-04-06
When your keyboard acts up, open a terminal:

```
dmesg | tail -100
```

Cut and paste any keyboard errors.

---

### Post by eyeneedhelp on 2013-04-06
does this mean anything?

"   9.407740] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.456015] wlan0: no IPv6 routers present
[  142.586242] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input10"


only when i turn off completly,cold, then turn on it blinks. i unplug and plug into the mouse port since im using a usb mouse.
the kbd then works.
ill try another kbd but this one is fine at this moment as i type this..

oh when i try to stretch the terminal i have a n
extremly hard time getting a grip on the corner or edge to pull it

---

