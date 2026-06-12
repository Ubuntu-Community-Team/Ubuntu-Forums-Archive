---
title: "strange kernel error... pardevice?"
date: 2007-01-01
forum: General Help
---

### Post by K3WHO on 2007-01-01
I'm runnind dapper and lately I've been getting this kernel error in my logs lately. It just seems to go on and on and on. 

```
 

--------------------- Kernel Begin ------------------------


 1 Time(s): [17436580.056000] ppdev0: registered pardevice
 1 Time(s): [17436580.104000] ppdev0: unregistered pardevice
 1 Time(s): [17436610.108000] ppdev0: registered pardevice
 1 Time(s): [17436610.156000] ppdev0: unregistered pardevice
 1 Time(s): [17436640.160000] ppdev0: registered pardevice
 1 Time(s): [17436640.208000] ppdev0: unregistered pardevice
 1 Time(s): [17436670.212000] ppdev0: registered pardevice
 1 Time(s): [17436670.260000] ppdev0: unregistered pardevice
 1 Time(s): [17436700.264000] ppdev0: registered pardevice
 1 Time(s): [17436700.312000] ppdev0: unregistered pardevice
 1 Time(s): [17436730.316000] ppdev0: registered pardevice

```

Does anyone happen to know what's going on? I'd appreciate any help cuz I'm flummoxed.

---

### Post by dannystaple on 2008-02-03
I am currently seeing this issue in Gutsy - did you find out what it was? 
I am using my machine with a USB HP 1317 Multi function device. Could it be that this device is trying to register an emulated parallel port device when I am scanning with it?
I have been doing a lot of scanning today.
I would like to be able to supress these messages in my dmesg, as it is masking some other messages I am actually looking for.

---

