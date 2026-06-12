---
title: "simple ndiswrapper question"
date: 2005-06-03
forum: General Help
---

### Post by mr.me on 2005-06-03
do you need to use the "-d devid driver   Use installed 'driver' for 'devid'"  command to get your card to work? and if so how do I find out what my "pciID" is?

thanks

---

### Post by drummer on 2005-06-03
[QUOTE=mr.me]do you need to use the "-d devid driver Use installed 'driver' for 'devid'" command to get your card to work? and if so how do I find out what my "pciID" is?

thanks[/QUOTE]
 Hi, pciID can be fould using lspci from the command line.
Once ndiswrapper is installed you install the driver with ```
sudo ndiswrapper -i *.inf
``` then check it installed correctly with ```
ndiswrapper -l
```which should give you something like this:
```
$ ndiswrapper -l
Installed ndis drivers:
wg311v2 driver present, hardware present
```then load the ndiswrapper module with ```
sudo modprobe ndiswrapper
```
Once you've confirmed the driver installed properly and is working properly, add the module to /etc/modules with```
sudo ndiswrapper -m
```so that it loads at boot.
hope it all works for you.. (I was thrilled when I finally got my wireless up. :))

---

