---
title: "Scanner Epson V30 Ubuntu 14.04"
date: 2014-04-26
forum: General Help
---

### Post by daniell59 on 2014-04-26
I presently have Ubuntu 12.04 64. I am thinking of a clean install to 14.04 64. I don't remember how I installed the drivers when I installed my present version. I would appreciate it if someone would refresh my memory.

Thanks

---

### Post by rbmorse on 2014-04-26
You can get the iscan/driver package from [http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult).  You'll need two files (core and data package and the scanner driver) .  Click where indicated and follow the prompts.  

For the core package and data package, once you accept the T's and C's you'll get another page that lists the available files.  The one you want is:

[COLOR=#333333][FONT=Tahoma]iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb

or [/FONT][/COLOR][COLOR=#333333][FONT=Tahoma]iscan_2.29.3-1~usb0.1.ltdl7_i386.deb
[SIZE=2]
depending upon your architecture.[/SIZE] [/FONT][/COLOR]

---

### Post by DrPotoroo on 2014-04-29
After weeks of problems with this I have successfully installed the epson drivers. Although there are 64 bit drivers available, some packages weren't installing for me and I think adding i386 architecture to install skye may have been the change that allowed these to install. If not that, it may have been finally stumbling on the right order to do things.
```
sudo dpkg --add-architecture i386
```

The other aspect to getting it to work was found here: [http://askubuntu.com/questions/209795/epson-xp-605-printer-driver-for-ubuntu](http://askubuntu.com/questions/209795/epson-xp-605-printer-driver-for-ubuntu)
The key was editing /etc/sane.d/epkowa.conf per those instructions and adding the IP address of the device.

---

