---
title: "Printer almost installed, just dont know how to install this file..."
date: 2013-06-20
forum: General Help
---

### Post by azitizz on 2013-06-20
I am trying to install a Brother 495-cw printer. Ive been trying to follow a number of tutorials on how to install certain packages and create directories, and as an amateur Linux user Im always stumped by an error message in terminal that I dont know how to get around.

Simplest for me is using the GUI "add printer" option in the settings. I have a ppd file on my desktop I downliaded from brother, and Im taken through the install process up to a point what it asks for the ppd file, I find it and go forward, then I get this message:

***Printer 'Brother-MFC-495CW' requires the '/usr/lib/cups/filter/brlpdwrappermfc495cw' program but it is not currently installed.  Please install it before using this printer.***

How do I do this? 

Thanks if anyone can help.
M

---

### Post by grahammechanical on 2013-06-20
It is looking for bripdwrappermfc495 at /usr/lib/cups/filter/. You could use file manager to look for it. Is it where it should be? Is it somewhere else? If you find it you may need administrator privileges to copy it into that cups folder.

By the way, did you also download and install the cupswrapper driver?

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW)

The software centre has brother printer drivers. Select a driver and click on more info and see all the models covered by that driver. I did not find one for your model but another one may work almost as well.

Regards.

---

### Post by Don Barzini on 2013-06-20
Try this....

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html)

You may need to install this package too ...... (linux-brprinter-installer)

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.4-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.4-1.gz&lang=English_lpr)

---

### Post by azitizz on 2013-06-20
> **grahammechanical said:**
> It is looking for bripdwrappermfc495 at /usr/lib/cups/filter/. You could use file manager to look for it. Is it where it should be? Is it somewhere else? If you find it you may need administrator privileges to copy it into that cups folder.

By the way, did you also download and install the cupswrapper driver?

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW)

The software centre has brother printer drivers. Select a driver and click on more info and see all the models covered by that driver. I did not find one for your model but another one may work almost as well.

Regards.


Yes I did install the cupswrapper driver. Didnt seem to work...

Thanks for the replies.

The bripwrappermfc495 file wasnt at usr/lib/cups/filter/ I did a search with nothing turning up. I tried googling it too but nothing, so Im not sure where to get and how to install this file/program.

---

