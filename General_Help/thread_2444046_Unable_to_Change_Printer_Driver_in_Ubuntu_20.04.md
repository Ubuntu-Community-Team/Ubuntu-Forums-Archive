---
title: "Unable to Change Printer Driver in Ubuntu 20.04"
date: 2020-05-23
forum: General Help
---

### Post by yetanotherbryan on 2020-05-23
I'm trying to get my printer setup on a fresh install of 20.04.  In setttings, when I add  my network printer (Samsung M287X), it is found and installs a default driver.  I am able to print normally.  I trying to swap out the printer driver ("Additional Printer Settings" > "Properties" > "Make and Model -Change") to install alternative drivers.   This is necessary to enable some features such as two sided printing.   When I click "Change" it attempts to search for drivers but comes unresponsive.  This is something that I have done many times on previous versions of ubuntu.  Anybody have an idea of what is happening here?  

Thanks,

Bryan

---

### Post by ardouronerous on 2020-11-04
> **yetanotherbryan said:**
> I'm trying to get my printer setup on a fresh install of 20.04.  In setttings, when I add  my network printer (Samsung M287X), it is found and installs a default driver.  I am able to print normally.  I trying to swap out the printer driver ("Additional Printer Settings" > "Properties" > "Make and Model -Change") to install alternative drivers.   This is necessary to enable some features such as two sided printing.   When I click "Change" it attempts to search for drivers but comes unresponsive.  This is something that I have done many times on previous versions of ubuntu.  Anybody have an idea of what is happening here?  

Thanks,

Bryan

I'm also experiencing this bug when I upgraded to Xubuntu 20.04 this week, so I made a bug report: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/1902858](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/1902858)

---

### Post by bobbena on 2021-04-10
To the person trying to change driver on your printer. I did it the old way by opening cups in a web page [http://localhost:631](http://localhost:631) log in with what you log into Ubuntu. You can do a lot there. Have my Dymo 4XL working great

---

### Post by kurt18947 on 2021-04-11
There is a Samsung printer/scanner driver found on HP support pages. I use it in order to have scanner support for a Samsung multifunction machine.

---

