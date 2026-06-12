---
title: "HP Compaq 8200 Elite Driver Problem"
date: 2016-11-16
forum: General Help
---

### Post by titanic1955 on 2016-11-16
Hallo everbody


I have  a HP **Compaq 8200 Elite USDT desktop** PC. 

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02781659](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02781659)


with intergrated Intel HD graphic (graphic memory 256 MB)


and often have problems with the graphic.


The screen often flickers when I am workingr.


HP und Intel was not able to help because it is Linux.


Maybe someone also has such an HP desktop?


Thanks for all support.

---

### Post by ajgreeny on 2016-11-16
Is that the only graphic card as the specs link you gave says they can also use an ATI Radeon HD 5450 (512MB) card?

---

### Post by titanic1955 on 2016-11-16
Hi Ajgreeny,

> **ajgreeny said:**
> Is that the only graphic card as the specs link you gave says they can also use an ATI Radeon HD 5450 (512MB) card?

I was also wondering the same thing.

When I bought the PC  it had Windows 7 on it with **Intel HD** driver

In the Terminal with command

 [B]lspci -nnk | grep "VGA\|'Kern'\|3D\|Display" -A2 

[/B]I get:

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
    DeviceName:  Onboard IGD
    Subsystem: Hewlett-Packard Company 2nd Generation Core Processor Family Integrated Graphics Controller [103c:1496]

:confused:

---

