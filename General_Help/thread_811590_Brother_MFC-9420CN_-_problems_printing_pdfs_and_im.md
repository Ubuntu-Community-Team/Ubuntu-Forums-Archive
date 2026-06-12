---
title: "Brother MFC-9420CN - problems printing pdfs and images"
date: 2008-05-29
forum: General Help
---

### Post by bkortleven on 2008-05-29
I have a Brother color laserprinter, type MFC-9420CN.
Printing works fine with the brother drivers and cupswrapper, (look here: [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de) for info and download) which all installed without any error.

Now, when printing from evince or acrobat, I get postscript errors, not handling certain objects or commands correctly.
It outputs a blank page with these marking on it:

Error Name;
Undifined
COMMAND;

OPERAND STACK;
--dicttype--
--booleantype--
--booleantype--


I contacted brother support, but they cannot find the issue...
We're running Ubuntu Desktop 7.04

When trying to use any other 'default' pcl driver for example the HP Color Laserjet 4550 or similar, we just get black and white prints, but the errors are gone...

Thanks for the help and info.

---

### Post by opscure on 2008-05-29
The PPD file that you are using with the cups driver is likely using BR-Script.  While this should process postscript fine, I have noticed some complaints and bugs reported throughout my travels.  You may want to give the postscript PPD a shot as opposed to the PPD found on your CD.  

You can find a listing of them here:
[http://solutions.brother.com/linux/sol/printer/linux/developers.html#2](http://solutions.brother.com/linux/sol/printer/linux/developers.html#2)

I can't say for certain that this will fix your issue or even work, but considering you can't print postscript documents, I think this might be a good place to start.

---

