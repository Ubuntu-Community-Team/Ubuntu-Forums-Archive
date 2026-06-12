---
title: "Brother printer"
date: 2013-01-22
forum: General Help
---

### Post by sunseeker17 on 2013-01-22
:) I am a new user of Ubuntu 12.01 and so far so good having used windows for years.Can someone help me get my Brother printer DCP-195c to work with Ubuntu 12.01 if possible? Or is it worth getting another printer that is compatible.
Cheers

---

### Post by Slimey on 2013-01-22
I bought a printer (on a massive special) and had to return it (much to my disappointment) because it wasn't compatible with Linux (Ubuntu). You might be in a similar position - having to get another printer. You might, however, be able to install a Linux-compatible printer driver (the software that links you computer to the printer). I made a quick google search, and (hopefully) found  a brother driver for you:


[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/dcp195clpr-1.1.3-1.i386.rpm&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/dcp195clpr-1.1.3-1.i386.rpm&lang=English_lpr)

Try accepting the agreement and installing the package (the thing that automaticaly downloads). You may have to seek advice on how to install packages if you don't know. 

Let me know how you go!

---

### Post by UltimateCat on 2013-01-22
These pages are  for the CupsWrapper driver. **If,** accepting the agreement and installing the package doesn't work.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1.html)

Once you download the driver you can install it using:
```
apt-get install <name of driver>

```
Hope this helps

---

### Post by sunseeker17 on 2013-01-22
:D Thanx ultimate cat. Seems to work so far.

---

