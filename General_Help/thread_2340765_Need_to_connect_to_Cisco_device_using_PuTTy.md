---
title: "Need to connect to Cisco device using PuTTy"
date: 2016-10-21
forum: General Help
---

### Post by jburges2 on 2016-10-21
Firstly, I apologize for my ignorance, as I haven't touched a Linux distro in eons, and have forgotten how to do pretty much everything.

That being said, I have an older Laptop using Lubuntu (16.04.1 LTS) that does not have a Serial port. I have a possible job coming up to console into a couple devices, and wanted to make sure I got the general gist before heading out. I do not have the exact model numbers of said Cisco devices yet, but wanted to know if I could achieve consoling into the devices with my current setup using a the [RJ45 to RJ45 rollover cable]("https://www.cdw.com/shop/products/Tripp-Lite-Cisco-Console-Replacement-Rollover-Cable-RJ45-32AWG-M-M-6ft-6ft/4096921.aspx?cm_cat=GoogleBase&cm_ite=4096921&cm_pla=NA-NA-TRI_CN&cm_ven=acquirgy&ef_id=WAqiwQAAAXiv2BBa:20161021232033:s&gclid=CjwKEAjw-abABRDquOTJi8qdojwSJABt1S1OoNaMn0FvALImH3HCpSUOS8u_4rrDidA0HaI3WwcEsBoCahbw_wcB&s_kwcid=AL!4223!3!61836302419!!!g!18283950120!") to connect, and would I need to configure anything special since I am not using the usual COM1 serial port?

I have not needed to connect to a device using the traditional DB9 to RJ45 connector in years, and even when I did, I had a laptop back then that DID have a serial port. Thanks in advance for helping, and please be gentle, lol.

---

### Post by TheFu on 2016-10-21
If you need a serial console connection, get a USB-2-serial converter ($10) and use minicom.

Putty from Windows is an ssh client (to my knowledge), so you can use ssh from any *nix machine, including ubuntu to make that sort of connection.

---

### Post by jburges2 on 2016-10-22
> **TheFu said:**
> If you need a serial console connection, get a USB-2-serial converter ($10) and use minicom.

Putty from Windows is an ssh client (to my knowledge), so you can use ssh from any *nix machine, including ubuntu to make that sort of connection.

So would the crossover cable I linked not work?

Also, does anyone know of a link or have reference material for configuring putty?

Lastly, what can I use to see what /dev/tty# is associated with what port? I know that /tty0 is usually associated with com1 (serial), but that is about all I know.

---

