---
title: "Install printer driver with only Commandline"
date: 2008-03-08
forum: General Help
---

### Post by zoomiest on 2008-03-08
Having looked around, I can't find any answers - I have to ask directly.

I am the latest Samba server - with no GUI - and have configured it to share files nicely.
I have CUPS installed (it tried to download it again, but it said I have the latest already)

But, how do I use CUPS to install the driver?

Does CUPS have an auto-install feature? How do I install a driver from the CUPS database?

(What I have done so far, is download the driver from the vendor's website, and upon installing every library it asks for, it now just says "contact customer support" and its Saturday night...

My Samsung ML-4500 is likely in the CUPS database...  Please help. I am leaving town on Monday... would like to get this taken care of...

---

### Post by x1a4 on 2008-03-08
Hi,

The driver you downloaded, is it a deb?  If so, you can install it like this:
```
sudo dpkg -i /path/to/printer/driver.deb
```
And if it's RPM:
```
sudo alien -idc /path/to/printer/driver.rpm
```

You can also manage CUPS using a console web browser like **lynx**, **links**, or **elinks**. 

Also, lookup **cupsaddsmb** which adds printers to samba;  **cups-genppd.5.0** used to generate PPDs from the CUPS database, and its corresponding config tool **cups-genppdconfig.5.0**

CUPS tools are located in **/usr/sbin/**--have a look in there and man the various applications.  

Sorry I couldn't be of more help.  Good luck.

---

