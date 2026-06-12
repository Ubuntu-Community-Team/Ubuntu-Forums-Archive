---
title: "Does Ubuntu provide any substitute for Excel?"
date: 2016-04-06
forum: General Help
---

### Post by mringer on 2016-04-06
My PC is dual boot. The Windows side has given me grief, and recently
packed up completely.  I would gladly abandon Windows, but I have several Excel 
files with macros that do a whole range of useful jobs. I have tried:

Excel in Wine. This provides the minimal functions of entering data and 
on-spreadsheet formulae, but if  I try to run any macro, it crashes.

Excel in Win XP in Virtual box. Excel wont install. I think this is actually 
a Windows problem. 

Re-install XP on its partition. Same problem. 

Open office. Wont run Excel VBA. Also, I have never been able to write a macro
from scratch, I have always had to record something and then edit the result. 
If in Excel I record some simple actions, I get a simple macro. In OO the same
actions give something far more messy and complicated. Also, the online help
for OO is hopelessly inadequate. Translating my macros into OO would be a 
nightmare.

I know there are several other Office programs, but please does any of these 
run Excel macros?

 Thank you.

---

### Post by The Cog on 2016-04-06
There is LibreOffice calc or gnumeric. I use and recommend calc. LibreOffice is available for windows too if you care to try it there. t can do .xls and .xlsx as well as its native .ods (which Excel also tries to do).

---

### Post by kurt18947 on 2016-04-06
OO/LibreOffice are known to not run VBA. It seems like I've read about an offshoot of OO/LO that has VBA enabled but I don't recall details. It might be worth looking at KingSoft Office. It has a reputation for very good MSO compatibility though I don't know about macros and have no experience with it. I've been able to avoid MSO to date. Here are a couple links to peruse re excel macros & LO/OO:

[http://www.debugpoint.com/category/programming/libreoffice/](http://www.debugpoint.com/category/programming/libreoffice/)

[https://ask.libreoffice.org/en/question/36699/how-to-convert-macro-of-vba-of-ms-excel-to-libreoffice-calc/](https://ask.libreoffice.org/en/question/36699/how-to-convert-macro-of-vba-of-ms-excel-to-libreoffice-calc/)

Not very hopeful news, I'm afraid.

I'm surprised you couldn't get Windows and Excel to install in a VM. I haven't tried MSO in a VM but WordPerfect seems to run fine on a Windows guest via Virtualbox.

---

### Post by montag dp on 2016-04-06
I'm afraid that if you want support for VBA macros you will need to use the actual Excel.  At least, that's been my experience, though I don't use Excel on my personal machine anymore.  But it is surprising that you couldn't get it to install on XP.  Maybe the MS Office version is too new?

---

### Post by mastablasta on 2016-04-07
MS 2010 has gold rating in wine. are macros still not working there?

what office version are you looking the alternative for?

---

### Post by dragonfly41 on 2016-04-08
I'm not a frequent user of macros in Windows Excel or LibreOffice Calc.
But I've been experimenting with Actionaz in Ubuntu for external automation of desktop apps workflows instead of using internal macros.

[http://www.webupd8.org/2014/03/automate-tasks-in-linux-using-actionaz.html](http://www.webupd8.org/2014/03/automate-tasks-in-linux-using-actionaz.html)

Also found under .. Applications > Accessories > Actionaz

Here is list of Actionaz actions.

[https://wiki.actiona.tools/doku.php?id=en:actions](https://wiki.actiona.tools/doku.php?id=en:actions)

First basic testing allows various operations to be executed on spreadsheet LibreOffice Calc.
And it seems easier to use than macros.

Actionaz is similar to AutoHotKey in Windows. And it runs in Windows or Linux.

---

