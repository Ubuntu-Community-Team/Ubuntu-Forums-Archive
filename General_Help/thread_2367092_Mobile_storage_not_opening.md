---
title: "Mobile storage not opening"
date: 2017-07-25
forum: General Help
---

### Post by Jeyaprakash on 2017-07-25
I am on ubuntu 16.04.2 (32 bit). I recently installed it and everything was fine. After installing all the updates available, the modem started giving problem at times (I reported it in another post) and the mobile storage is not getting recognised. I am posting details of it here. This is what comes with usb-devices command:

```

T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=04 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bb4 ProdID=0001 Rev=02.55
S:  Product=GIONEE P2
S:  SerialNumber=IFU4YL7HJBUKJNKR
C:  #Ifs= 0 Cfg#= 0 Atr= MxPwr=
cat: '/sys/bus/usb/devices/usb3/3-4/3-*:?.*/bInterfaceNumber': No such file or directory
cat: '/sys/bus/usb/devices/usb3/3-4/3-*:?.*/bAlternateSetting': No such file or directory
cat: '/sys/bus/usb/devices/usb3/3-4/3-*:?.*/bNumEndpoints': No such file or directory
cat: '/sys/bus/usb/devices/usb3/3-4/3-*:?.*/bInterfaceClass': No such file or directory
cat: '/sys/bus/usb/devices/usb3/3-4/3-*:?.*/bInterfaceSubClass': No such file or directory
cat: '/sys/bus/usb/devices/usb3/3-4/3-*:?.*/bInterfaceProtocol': No such file or directory
/usr/bin/usb-devices: line 79: printf: (none): invalid number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=() Sub= Prot= Driver=
```

Let me know if any further information is required. If you could give the code, I can type it in terminal and post results. Any help is welcome. Hope it is something to do with the new update of kernel or something..  hope it gets fixed.

---

### Post by Jeyaprakash on 2017-07-25
Ah, something became smileys.. ha ha.. It was actually ':' & '?' without any space there.

---

### Post by deadflowr on 2017-07-25
> **Jeyaprakash said:**
> Ah, something became smileys.. ha ha.. It was actually ':' & '?' without any space there.

Fixed that for you.
You needed to use the Go Advanced or Reply to Post option and near the bottom of the page in the additional options section is a disable smileys.
(Or it should be, not sure if it's staff-only function or not.)

---

### Post by Jeyaprakash on 2017-07-26
Thank you for fixing it. I see an option disable smileys. Did not notice that earlier. Coming to the forum after a very long time.. :)

---

### Post by QIII on 2017-07-26
Better yet to use code tags to preserve formatting and make your post more readable.  :)

---

### Post by Jeyaprakash on 2017-07-26
> **QIII said:**
> Better yet to use code tags to preserve formatting and make your post more readable.  :)

Thanks. Next time will try to use that.

---

