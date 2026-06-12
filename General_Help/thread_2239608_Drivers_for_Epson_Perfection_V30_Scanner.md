---
title: "Drivers for Epson Perfection V30 Scanner"
date: 2014-08-14
forum: General Help
---

### Post by daniell59 on 2014-08-14
Presently I have Ubuntu 12.04 64. I would like to clean install to 14.04. I cannot remember how I installed the scanner drivers. It is working perfectly. I would hate to install 14.04 and lose the scanner.

Thanks

---

### Post by rbmorse on 2014-08-14
You can download the Linux drivers and supplemental files (in necessary) from epson.com.  Select download drivers and follow the prompts.  Eventually (it takes a while) you'll get to the linux driver download page. The two files you want for 64-bit Ubuntu are:

 [COLOR=#333333][FONT=Tahoma]iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb
[/FONT][/COLOR][COLOR=#333333][FONT=Tahoma]iscan-data_1.29.0-2_all.deb

If you are running a 32-bit version of Ubuntu,  get

[/FONT][/COLOR][COLOR=#333333][FONT=Tahoma]iscan_2.29.3-1~usb0.1.ltdl7_i386.deb
[/FONT][/COLOR][COLOR=#333333][FONT=Tahoma]iscan-data_1.29.0-2_all.deb

Double-click to install. [/FONT][/COLOR]

---

### Post by daniell59 on 2014-08-27
I installed iscan_2.29.3-1~usb0.1.ltdl7_i386.deb and iscan-data_1.29.0-2_all.deb and the scanner is not detected. It even indicated in the software section that it was installed. Any additional assistance will be appreciated.

---

### Post by daniell59 on 2014-08-27
Just figured it out!

I also needed to install the following driver. esci-interpreter-gt-f720_0.1.1-2_i386.deb

---

### Post by linfidel on 2014-09-11
That driver is hard to locate.  I finally found it on the Epson site; there are two drivers listed that are not RPMs.  The first, and newest, one is the driver and data file we know about.  The second, and oldes, one is this esci file.

---

