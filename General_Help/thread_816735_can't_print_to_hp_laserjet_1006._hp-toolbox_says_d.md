---
title: "can't print to hp laserjet 1006. hp-toolbox says document printed, but it didn't."
date: 2008-06-03
forum: General Help
---

### Post by tphyahoo on 2008-06-03
On hardy heron, printing to hp laserjet 1006, hptoolbox installed, foo2zjs installed from source from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/).

My laptop detects the printer when I plug in the usb. It appears to install it.

I attempt to print a document. 

I get a "document print status" dialog indicating that the job has been completed on laserjet 1006. But it wasn't.

In hptools I choose view -> show printer status

In this printer status window, the laserjet 1006 is not listed. In fact, nothing is listed.

Any advice?

---

### Post by mbaker824 on 2008-06-03
> **tphyahoo said:**
> On hardy heron, printing to hp laserjet 1006, hptoolbox installed, foo2zjs installed from source from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/).

My laptop detects the printer when I plug in the usb. It appears to install it.

I attempt to print a document. 

I get a "document print status" dialog indicating that the job has been completed on laserjet 1006. But it wasn't.

In hptools I choose view -> show printer status

In this printer status window, the laserjet 1006 is not listed. In fact, nothing is listed.

Any advice?


If you run System->Administration->Printing, do you see any printers set up?  I'm guessing you won't, so click on New Printer, and it should detect your printer; out of the box, Ubuntu 8.04 has automatically detected every HP printer I've thrown at it, including network printers.

At that point, you should be able to just follow the bouncing ball through the rest of the setup. If not, post here again with any additional details, such as error messages.

BTW, there's no need to install foo2zjs from source - it's available in the Ubuntu repositories, and it's generally better to install that way whenever possible, so updates are readily and easily available.

Mark

---

