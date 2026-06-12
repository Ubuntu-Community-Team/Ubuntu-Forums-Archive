---
title: "Page Printing"
date: 2017-05-23
forum: General Help
---

### Post by colinyorke on 2017-05-23
I have installed Lubuntu 14 on my computer that originally had Windows 7. Connected to this computer is a Brother DCP-145C printer & I installed the software from Brother to enable it to print & scan. This seems to work apart from the following, when printing using A4 paper about 10 to 15mm of printing is missing from the top of the page. I have looked in the setting to see if I can adjust them but to no avail. Is there any way to correct this?
When using the same printer with Windows 7 it is OK.

---

### Post by Bucky Ball on 2017-05-23
Welcome. How did you install the driver? Did you use the [Brother driver install tool from here]("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=dcp145c_eu_as&os=128")? Once you'd installed the driver, did you open 'Printers' and 'Add Printer' there, selecting the driver you installed when you got to that section of the 'Add Printer' process?

---

### Post by ajgreeny on 2017-05-23
I had this same problem some time ago with another Brother printer and eventually found a solution for which I quickly created a note and kept just in case.  Your problem may be totally different, of course, but here's my note related to my own printer; change the model etc etc, as necessary for you, and good luck.
> Incorrect margin settings can be caused by an incorrect paper size setting.

1. If you are using OpenOffice (e.g. OpenOffice Word Processor), change the document size in "Menu -> Format -> Page" to match your paper size.

2. Change the paper size setting from the cups web interface "http://localhost:631/printers" -> "Set Printer Options")

3. Edit the paper size parameter in 
/usr/local/Brother/inf/brmfc5860rc
or
/usr/local/Brother/Printer/(model name)/inf/br(model name)rc
or
/usr/Brother/Printer/mfc5860cn/inf/brmfc5860cnrc
to the paper size.
***The available parameter value is in the /etc/cups/ppd/(model name).ppd file.
***This action will change the default printout paper size.

---

### Post by colinyorke on 2017-06-25
Thank you did as you advised & also changed paper type in driver configuration, now working OK.

---

### Post by colinyorke on 2017-06-25
Thank you working OK now.

---

### Post by Bucky Ball on 2017-06-25
Good news. To help others, please mark the thread as solved by using 'Thread Tools' at the top right of the page. Enjoy. ;)

---

