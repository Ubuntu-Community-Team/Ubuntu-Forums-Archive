---
title: "How to read an USB Smart Card?"
date: 2008-03-13
forum: General Help
---

### Post by piousp on 2008-03-13
Does anyone know how to?

This is the output of lsusb

```

Bus 002 Device 002: ID 04b9:1202 Rainbow Technologies, Inc. iKey 2032 Token

```
I did a quick google, but i didnt recognize something usable

Here is more info on /proc/bus/usb/devices
```

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04b9 ProdID=1202 Rev= 1.00
S:  Product=iKey 2032
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 56mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

```

---

