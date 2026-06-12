---
title: "Verizon USB551L workaround"
date: 2013-04-23
forum: General Help
---

### Post by junkfactory on 2013-04-23
Been banging my head for a few hours now and it seems wvdial is the only way I can get this damn USB modem to work in ubuntu.

Heres my wvdial.conf

```

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99***3#
ISDN = 0
Username = <yournumber>@vzw4g.com
Init1 = ATZ
Password = vzw
Modem = /dev/ttyUSB0
Baud = 9600
Stupid Mode = 1

```

I had no such luck using the NetworkManager

Anyone got this to work in NetworkManager?

---

