---
title: "Xerox Drivers for WCP problem...."
date: 2005-08-30
forum: General Help
---

### Post by offishall on 2005-08-30
Hey guys. I just switched to Ubuntu and am liking it alot, but now when I tried to install the driver package for Xerox WCP machines, I get
........................ERROR: No such file or directory.

I am a fairly newbie, is there a way to log what the ./setup is doing so I can see where it is failing?

[Linux Intel Driver](http://www.support.xerox.com/go/results.asp?Xlang=en_US&XCntry=USA&prodID=WCP245_WCP255&ripId=&Xtype=download)

---

### Post by arnieboy on 2005-08-30
[QUOTE=offishall]Hey guys. I just switched to Ubuntu and am liking it alot, but now when I tried to install the driver package for Xerox WCP machines, I get
........................ERROR: No such file or directory.

I am a fairly newbie, is there a way to log what the ./setup is doing so I can see where it is failing?

[Linux Intel Driver](http://www.support.xerox.com/go/results.asp?Xlang=en_US&XCntry=USA&prodID=WCP245_WCP255&ripId=&Xtype=download)[/QUOTE]
there should be an error log created in the same directory that u are installing it from. have u checked?

---

### Post by offishall on 2005-08-31
nothing there .....

---

### Post by offishall on 2005-09-06
As much as I hated to do it, I had to kill Ubuntu and go with Mandriva, all working now. Maybe if they get it working in the next version we will go with Ubuntu.

Thanks

---

### Post by hellomatts on 2007-06-06
I know this is two years later, but I just got off the phone with Xerox and they walked me through the process of adding a Work Centre Pro (32 in my case) but this should work for all models:

1. Go to the xerox website and download the WinXP Generic PPD driver

2. edit the file as sudo and remove the following line: "*cupsFilter: "application/vnd.cups-postscript 0 XeroxWCPFilter"

3. copy the edited file into /etc/cups/ppd

4. restart the cups service : $ sudo /etc/init.d/cupsys restart

5. install the printer as you would system>Administration>Printing - the driver should appear in the list, otherwise, click on the Add driver button and find your edited PPD file.

Hopefully this will help others to print with a Xerox WCP...

---

### Post by jodoj80 on 2007-12-06
Thx hellomatts. This steps help me install a XRWCP 232 really fast and easy in Gusty.

---

### Post by slick666 on 2008-01-22
Yeah, Thanks

I used the same method to setup a Workcenter 7665P. I didn't have to edit the PPD file though. It didn't contain the "*cupsFilter:" line.

---

