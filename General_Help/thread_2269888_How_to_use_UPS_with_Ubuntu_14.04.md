---
title: "How to use UPS with Ubuntu 14.04"
date: 2015-03-18
forum: General Help
---

### Post by kkrassi1984 on 2015-03-18
[COLOR=#333333][FONT=UbuntuRegular]Hello I have a UPS but can not see what procedure the battery and how to remain percent spending. Here I attach some photos looks like the battery of Ubuntu 14.04[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][IMG]http://i.stack.imgur.com/wVwuA.png[/IMG]

The battery once it exists, and then disappears and then appears again. Here's how it looks and statistics Power Statistics. [/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][IMG]http://i.stack.imgur.com/l8CNz.png[/IMG][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]how I wanted to run this UPS to see normal battery, but not red and blinking so. Model and brand are the following[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]EATON 5E 850V/480W.

[/FONT][/COLOR]I apologize if the topic is not for this section.

---

### Post by plurga on 2015-03-18
pls check if u hw pc is supported to work with this kinda UPS !

---

### Post by kkrassi1984 on 2015-03-19
Under Windows have no problem showing me how long rates to charge how loaded everything normal, but under Ubuntu have this problem.

---

### Post by SeijiSensei on 2015-03-19
I don't see any software on Eaton's site that supports Linux.  I always use APC's because they are well-supported by the **apcupsd** package.

---

### Post by kkrassi1984 on 2015-03-19
What is APC, some company? Also if you install this package **apcupsd** this mean that you will have a chance to go to statistics for UPS ?

---

### Post by SeijiSensei on 2015-03-19
[APC]("http://www.newegg.com/APC/BrandStore/ID-1317") is an American manufacturer of UPS's.  The apcupsd package is a third-party open-source utility to manage those devices.  My guess is that it won't work with a product from Eaton unless they offer the same software interfaces that APC does.  You can try installing a copy from the repositories and see if it works with your device.

Eaton offers its "[UPS Companion](http://powerquality.eaton.com/EMEA/Products-services/Power-Management/Software-Drivers/UPS-Companion.asp)" software, but it only runs on Windows.

As a general rule, you should not expect devices like these to be supported in Linux unless the manufacturer provides compatible software, or you know that a third-party utility exists that supports them.  I see that Eaton claims its products "support" Linux, but that doesn't necessarily imply software utilities.  It may mean only that if you plug a Linux computer into the device, and the power goes off, the UPS will function as expected.  Lots of home routers are advertised as "supporting" Linux, but usually that just means you can connect a Linux computer into one of their network ports or via wifi, not that they have any special hardware or software designed for Linux.

---

