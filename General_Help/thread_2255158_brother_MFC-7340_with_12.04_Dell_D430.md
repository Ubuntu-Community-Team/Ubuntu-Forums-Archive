---
title: "brother MFC-7340 with 12.04 Dell D430"
date: 2014-12-02
forum: General Help
---

### Post by elim-qiu on 2014-12-02
Downloaded mfc7340 printer installer from Brother,  brmfc7340lpr-2.0.2-1.i386.deb, installed with Ubuntu Software Center. Then test it for a web page, LibOffice doc etc. All the same: endlessly printing out blank pages until run out of papers!

Any idea how to fix it?  This is a multi-boot laptop. xp, snow leopard and ubuntu 12.04. Only ubuntu has trouble with MFC-7340.

Thanks for your inputs!

---

### Post by plucky on 2014-12-02
> **elim-qiu said:**
> Downloaded mfc7340 printer installer from Brother,  brmfc7340lpr-2.0.2-1.i386.deb, installed with Ubuntu Software Center. Then test it for a web page, LibOffice doc etc. All the same: endlessly printing out blank pages until run out of papers!

Any idea how to fix it?  This is a multi-boot laptop. xp, snow leopard and ubuntu 12.04. Only ubuntu has trouble with MFC-7340.

Thanks for your inputs!

You also need to download and install the CUPS driver.

Open a terminal and post output for ```
dpkg -l | grep -i brother
``` will show what drivers are installed.

Good Luck

p.s. There is a [Driver Install Tool](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128) available on the Brother Website.

---

### Post by elim-qiu on 2014-12-02
Thanks a lot [COLOR=#000000]**plucky!**[/COLOR] I finally got it work using the install tool. 

It took me about 300Mb HDD space, lots lib updated/added? I cannot stop the process but really scare about that installation would upgrade 12.04 to 14.04:)

After that, it still not working, I run the 3 unintallation program the installer provided and re-run the installer. And it worked!

---

### Post by elim-qiu on 2014-12-02
elim@grace:~/Downloads$ dpkg -l | grep -i brother
ii  brmfc7340lpr:i386                      2.0.2-1                                 Brother MFC-7340 LPR driver
ii  brscan-skey                               0.2.4-1                                 Brother Linux scanner S-KEY tool
ii  brscan3                                      0.2.11-5                               Brother Scanner Driver
ii  cupswrappermfc7340:i386        2.0.2-1                                 Brother MFC7340 CUPS wrapper driver
ii  printer-driver-ptouch                  1.3-3ubuntu0.1                    printer driver Brother P-touch label printers

simple scan app not working.....

---

### Post by plucky on 2014-12-03
> simple scan app not working..... 

Have you installed sane-utils?

```
sudo apt-get install sane-utils
``` and then you might have to reboot.

Good Luck

---

### Post by pdc on 2014-12-03
plucky is giving you very good support but if I could add a question about the scanner: is the device wireless?

Brother provide this guide [http://support.brother.com/g/s/id/linux/en/instruction_scn1.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1.html?c=us_ot&lang=en&redirect=on) and for the scanner; and a usb connection; one needs to install a small file so the user can access the scanner; by default it is only sudo 

.............if wireless, some recommend a static IP address for the device .................

---

### Post by elim-qiu on 2014-12-04
> **plucky said:**
> Have you installed sane-utils?

```
sudo apt-get install sane-utils
``` and then you might have to reboot.

Good LuckThanks a lot plucky!

---

### Post by elim-qiu on 2014-12-04
> **pdc said:**
> plucky is giving you very good support but if I could add a question about the scanner: is the device wireless?

Brother provide this guide [http://support.brother.com/g/s/id/linux/en/instruction_scn1.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1.html?c=us_ot&lang=en&redirect=on) and for the scanner; and a usb connection; one needs to install a small file so the user can access the scanner; by default it is only sudo 

.............if wireless, some recommend a static IP address for the device .................

Thanks a lot pdc. MFC-7340 is not wireless. But there are wireless ones alone the MFC-7* series.

---

### Post by roger_1960 on 2014-12-04
Hi

If you still have trouble with the scanner working, do these things (from the Brother website [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us&lang=en&prod=mfc7340_us_as&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us&lang=en&prod=mfc7340_us_as&redirect=on) ).  I needed them with 14.04 as well - I dont think the Brother site has been updated.

Ubuntu 10.10, 11.4, 11.10, 12.04, 12.10, 13.04, 13.10
1. Click here to download the file.(brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1, 2KB)
2. Run the command.
Command: dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"". 

The lines to be added---------------------------

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
 
3. Restart the OS.

Hope that helps

Roger

---

