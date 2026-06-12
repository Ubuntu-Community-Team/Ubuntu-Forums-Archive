---
title: "Network printing: which driver(s) are used?"
date: 2012-12-18
forum: General Help
---

### Post by 2CV67 on 2012-12-18
I have a Canon printer connected by USB to my desktop PC running Ubuntu (Lubuntu) 12.04.
I have it installed 3 times with different names & different drivers: Canon, Gutenprint & TurboPrint (testing).
Other family members also use this printer from their laptops & netbooks, via the home wifi network.
The portables run Windows 7 & Vista.
Whenever we install any of the 3 network printers on the portables, Windows installs a Canon driver.

All this works (more or less well) but I am confused as to which driver(s) are being used & may need adjusting in case of difficulties.

For instance, if we are printing from LibreOffice on W7 via wifi to the  TurboPrint Canon printer on the Ubuntu desktop PC and we want to set/remove Duplex printing, do we attack LibreOffice or W7 or the W7 Canon driver, or Ubuntu or TurboPrint?
Having tried most of the above for various settings, I find the results unclear...

Could I find a description or a diagram somewhere, showing which driver(s) are active in network printing with a USB printer?

Thanks!

---

### Post by ajgreeny on 2012-12-18
Surely those settings can be adjusted when needed from the print dialog of the application in the OS that you are using, which I assume will point to the correct driver setup for that OS automatically.

---

### Post by 2CV67 on 2012-12-19
Yes, but the results are not always as expected.

Let's say for my own satisfaction I would like to understand whether, in the above case, I am using only the driver on the portable, or only the driver on the desktop, or a bit of both, or what?

I am surprised not to be able to find any explanation of this common configuration.

---

### Post by 2CV67 on 2013-02-04
Bump...

Let's say for my own satisfaction I would like to understand whether, in the above case, I am using only the driver on the portable, or only the driver on the desktop, or a bit of both, or what?

I am surprised not to be able to find any explanation of this common configuration.

---

### Post by 2CV67 on 2013-05-16
[SIZE=7][COLOR="#FF0000"]**Bump!!**[/COLOR][/SIZE]

Could I find a description or a diagram somewhere, showing which driver(s) are active in network printing with a USB printer?

Thanks!   :)

---

### Post by pdc on 2013-05-17
mon cher ami .............oh that all things were straightforward; you sound very frustrated and vexed; 

I shake my head trying to envisage how your system is setup:

I spent part of yesterday reading the readme.txt from Canon's UFR driver (now at version 2.6) and when you see the many variations that have been reported to them; that they diligently try to address in the readme; you realise how complex things are: 

One command that they recommend: (ensuring that the printer is connected and turned on!!) ..is....

> [COLOR="#FF0000"]sudo /usr/sbin/lpinfo -v[/COLOR]

If you want to explore settings in LibreOffice the command

> [COLOR="#FF0000"]/usr/lib/libreoffice/program/spadmin[/COLOR] can be of help to some;

___________________________________________________-

for network printing, is anything here 

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

of help to you?

---

