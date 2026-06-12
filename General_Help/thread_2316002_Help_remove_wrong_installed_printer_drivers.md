---
title: "Help remove wrong installed printer drivers"
date: 2016-03-04
forum: General Help
---

### Post by Stevenukas on 2016-03-04
Followed instruction on brother printer site,but the package contained 32 and 64 bit versions of drivers, so by mistake, I have installed way too many. I have found from command line :

```

-l | grep Brother
rc  brmfc7820nlpr:i386                          2.0.1-1                                    i386         Brother MFC-7820N LPR driver
ii  brscan2                                     0.2.5-1                                    amd64        Brother Scanner Driver
rc  cupswrappermfc7820n:i386                    2.0.1-2                                    i386         Brother MFC7820N CUPS wrapper driver
ii  printer-driver-brlaser                      3-3build1                                  amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                       1.3-8ubuntu1                               amd64        printer driver Brother P-touch label printers

```

How would I remove all drivers and start all over again. This might have been asked before, wasn't able to find.

---

### Post by Stevenukas on 2016-03-04
When using Synaptic managed to remove almost all of them. dpkg  -l  |  grep  Brother still shows 2 drivers ```
 
rc  brmfc7820nlpr:i386                          2.0.1-1                                    i386         Brother MFC-7820N LPR driver
rc  cupswrappermfc7820n:i386                    2.0.1-2                                    i386         Brother MFC7820N CUPS wrapper driver

```

tried to
```

sudo apt-get autoremove brother-mfc-7820n-lrp-driver
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by $yl9pAR%t on 2016-03-04
Try this:

```
sudo dpkg --purge <package_name>
```

...and to get package_name:

```
dpkg --info <file_name>
```

---

### Post by kurt18947 on 2016-03-05
Did Brother's installer create uninstall scripts? I usually rely on their installer script and there is/are uninstaller scripts that I run from a terminal.  iIn the interest of keeping them where I can find them again (hopefully) I create a Brother folder and keep the install & uninstall files/scripts in one place.

---

### Post by Stevenukas on 2016-03-29
> **kurt18947 said:**
> Did Brother's installer create uninstall scripts? I usually rely on their installer script and there is/are uninstaller scripts that I run from a terminal.  iIn the interest of keeping them where I can find them again (hopefully) I create a Brother folder and keep the install & uninstall files/scripts in one place.
I didn't bother at that time. Since printer broke down ;) it was pleasure to get a new one with wifi printing and simple installation. Thank you

---

