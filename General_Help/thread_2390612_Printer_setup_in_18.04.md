---
title: "Printer setup in 18.04"
date: 2018-04-30
forum: General Help
---

### Post by Tom_Carr on 2018-04-30
I have a brother HL-L2320D printer.
Ubuntu 14.04 could not connect to it until I downloaded and installed the driver from Brother

18.04 found the printer when I pluigged it in.  It prints text files and libre office files just fine.  
It does not print jpg or pdf files.  At the top of the screen it says "printing" but nothing happens.
I also tried opening a pdf file with libre office, and the same thing happened.

Should I install the downloaded driver from brother, or is there another solution?

---

### Post by pqwoerituytrueiwoq on 2018-04-30
I have a HL-2360DW (wired network connection)

i noticed the printer was already configured after installing

I am able to print pdf files with no issues, well at least the one i made with my my cups pdf printer
I printed a test page in my pdf printer and then printed the pdf to my HL-2360DW and it worked fine

I did a clean install of 18.04

---

### Post by Tom_Carr on 2018-05-01
I also did a clean install of 18.04.
I guess I can just try adding the driver.  The only reason I haven't already tried that is that I thought it might possibly cause some problem and I would have to reinstall ubuntu.  I thought there might be some other quick fix other than adding the driver.  I guess there isn't since no one has answered this thread with any fix.

---

### Post by pqwoerituytrueiwoq on 2018-05-01
IIRC they provide a 32bit deb package, this package can be removed and the installer makes a uninstall script
on a side note i no longer need any 32bit software :)
edit: the stock driver seems to not have support for the toner saver feature

---

### Post by Tom_Carr on 2018-05-02
I installed to downloaded driver and now it seems to be working OK.

For anyone in the future with this problem, here is where I got the driver:
[http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hll2320d_us_as](http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hll2320d_us_as)

Thanks for your help.

---

