---
title: "printer woes"
date: 2018-06-19
forum: General Help
---

### Post by Timothy_Cota on 2018-06-19
[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=f3244aa4ca&view=att&th=1641870522ff3df8&attid=0.1&disp=safe&realattid=ii_jils7ih20_1641870522ff3df8&zw[/IMG]

 
Running: acer aspire TC-105 desktop
OS: ubuntu 16:04
Memory: 7.6 GIB
Processor intel Core i5 -4460 CPU @3.20 GHz x 4
Graphics intel Haswell Desktop

I am trying to install my Brother MFC-J480DW on ubuntu 16:04.
I downloaded the installer package:
linux-brprinter-installer-2.2.0-1.gz   What am I doing wrong?

---

### Post by bodhin2 on 2018-06-19
not sure - but you may use synaptic and do a search for brother printer drivers.  maybe that will work.  new to ubuntu but generally lately a lot of printer drivers seem to be there.  however in an enlightenment distro i was using prior one had to install/download via synaptic the hplip driver.  for the hp wireless.  on new ubuntu - all 3 laptops needed no setup whatsoever.  maybe this will help.

also 2x when i did an update on the old distro. i had printer issues that printed the page small and to the left - no one could help but by reinstalling the hplip stuff it fixed it.   go figure.   just an added bit of experience.

---

### Post by Timothy_Cota on 2018-06-19
I re-tried installing the printer from the terminal. When I searched for the installer tool The message was "not a gunzip file" I don't know where to go from here.  the package is labeled .gz.

---

### Post by bodhin2 on 2018-06-19
are you  installing the printer or driver?  if you do it through synaptic - as far as my experience goes - it takes care of itself.

---

### Post by Frogs Hair on 2018-06-19
They appear to have .deb package that will open with Ubuntu software. There seems to be general LPR driver for Linux. Verify before installing

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj480dw_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj480dw_us_eu_as&os=128)

[http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj480dw_us_eu_as&os=128&dlid=dlf102093_000&flang=4&type3=559](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj480dw_us_eu_as&os=128&dlid=dlf102093_000&flang=4&type3=559)

---

### Post by bodhin2 on 2018-06-19
a bunch of the drivers appear in synaptic too.  searched under lpr drivers pulls up a bunch.  not trying to confuse or send you down a rabbit hole.  but ut seems available.  that is my last bit of help. good luck.

---

