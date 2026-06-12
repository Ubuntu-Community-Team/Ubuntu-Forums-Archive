---
title: "Printers fully supported by ubuntu 14.04"
date: 2016-05-17
forum: General Help
---

### Post by ebinmathewtherattil on 2016-05-17
I'm planning to buy a new all in one  printer(home use) probably one with Wi-Fi, I need to know which company/model has good support for ubuntu. Pls help me .....

---

### Post by Linuxisfast on 2016-05-17
You are very safe with basically all HP models and I would suggest you use latest 16.04 LTS. For others use 14.04 or wait for Canonical to fix the LSB issue in latest 16.04

---

### Post by ebinmathewtherattil on 2016-05-18
I have shortlisted these three printers
HP M126nw LASERJET PRO, Canon MF-4720W, Brother DCP-1616NW
hp seems good now

---

### Post by Linuxisfast on 2016-05-18
HP will work right out of the box for you, in print quality and performance Epson rules and most work with built in escpr driver in Ubuntu.

---

### Post by ebinmathewtherattil on 2016-05-18
> **Linuxisfast said:**
> HP will work right out of the box for you, in print quality and performance Epson rules and most work with built in escpr driver in Ubuntu.
THANK YOU Linuxisfast

---

### Post by sudodus on 2016-05-18
I have a Brother HL-2250DN printer, and it works in 16.04 without tweaking, so Brother is a third alternative. (I don't know about newer Brother printers.)

---

### Post by SeijiSensei on 2016-05-18
CUPS has drivers for most Brother printers, though I have also used Brother's own "Printer Install Tool" available from the online download page for each model.  For multi-function devices this is probably a better choice since it will install both the scanner and printer drivers.  (I have an [HL-3170CDW]("http://www.newegg.com/Product/Product.aspx?Item=N82E16828113832").)

---

### Post by kurt18947 on 2016-05-18
> **SeijiSensei said:**
> CUPS has drivers for most Brother printers, though I have also used Brother's own "Printer Install Tool" available from the online download page for each model.  For multi-function devices this is probably a better choice since it will install both the scanner and printer drivers.  (I have an [HL-3170CDW]("http://www.newegg.com/Product/Product.aspx?Item=N82E16828113832").)

+1 for Brother and their installer script. Samsung seems quite good as well. I have a recent Samsung laser MFD and the printer will work using Foomatic drivers. The scanner didn't but both printing and scanning work very well using Samsung's linux driver. Duplex printing works in spite of some reviewers on Amazon claiming it doesn't. The list of printers and scanners that don't install and work easily these days seem quite a bit shorter than the list of those that do. If you want to do a 'manual' install for your brother printer, here are the linux drivers:

[http://support.brother.com/g/s/id/linux/en/download_prn.html#HL-3170CDW](http://support.brother.com/g/s/id/linux/en/download_prn.html#HL-3170CDW)

Here's the installer script:

[http://support.brother.com/g/b/agreement.aspx?dlid=dlf006893_000&c=us_ot&lang=en](http://support.brother.com/g/b/agreement.aspx?dlid=dlf006893_000&c=us_ot&lang=en)

---

