---
title: "Samsung Battery Life Extender?"
date: 2012-12-30
forum: General Help
---

### Post by KayeNg on 2012-12-30
Hi guys! In Windows 7, I can run Samsung BatteryLifeExtender.exe

It has the option to set the charging limit to 80% if the laptop is always using AC, and you can set it back to 100% if you're planning to use it outdoors.

I don't think I can run this in Lubuntu.  Any way around this? Or should I just boot into Windows partition and access the battery life extender from there?

Thanks guys!!!

---

### Post by 2F4U on 2012-12-30
It is unlikely that you can run BatteryLifeExtender on Ubuntu, since it is a Windows application. I am more familiar with IBM/Lenovo laptops, which have the same feature. There is a kernel module available (tp_smapi) for these laptops, which makes the feature accessible to the operating system and which allows to set start and stop battery charge thresholds.
However, I haven't found something similiar for Samsung laptops.

---

### Post by Linuxisfast on 2012-12-30
TLP does that for Lenovo/IBM laptops, if Samsung uses same method, that should do the trick as well.

---

### Post by KayeNg on 2012-12-31
> **linuxisfast said:**
> tlp does that for lenovo/ibm laptops, if samsung uses same method, that should do the trick as well.

tlp?

---

### Post by Linuxisfast on 2012-12-31
> **KayeNg said:**
> tlp?


[http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)

---

### Post by 2F4U on 2012-12-31
> **Linuxisfast said:**
> TLP does that for Lenovo/IBM laptops, if Samsung uses same method, that should do the trick as well.

The battery control feature are implemented by tp_smapi and are independent from TLP:

[http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)

---

### Post by KayeNg on 2013-01-01
> **2F4U said:**
> The battery control feature are implemented by tp_smapi and are independent from TLP:

[http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)

Does that mean I should do the tp_smapi thing before the TLP?

Sorry guys I'm really new to this.

---

### Post by faktor4u on 2013-01-01
> **KayeNg said:**
> Hi guys! In Windows 7, I can run Samsung BatteryLifeExtender.exe

It has the option to set the charging limit to 80% if the laptop is always using AC, and you can set it back to 100% if you're planning to use it outdoors.

I don't think I can run this in Lubuntu.  Any way around this? Or should I just boot into Windows partition and access the battery life extender from there?

Thanks guys!!!

AFAIK this option should be in BIOS. I have Samsung NP-RF511 and I can set charging limit to 80% in BIOS.

---

### Post by linrunner on 2013-01-13
Hi,

tp-smapi won't work with your Samsung. You may take a look into your BIOS setup for an option to set battery charge thresholds.

TLP will help you to save battery power though.

---

