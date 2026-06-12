---
title: "HP Photosmart c4240 All-In-One Help"
date: 2007-08-29
forum: General Help
---

### Post by dreamyseahorse on 2007-08-29
Hello-

I have Feisty Fawn (7.04) and Windows Vista on my computer. My HP Photosmart C4240 All-In-One printer works fine in Windows but I tried to add the printer on Ubuntu and even though it recognized it I couldn't find it in the list. It might be a stupid question but I have looked everywhere and can't find if I should sign up for Photosmart C4100 (the closest listed as an option) or if I should install some kind of file to make it compatible. Any suggestions?

---

### Post by linuxwizard on 2007-08-29
Check and see what version HPLIP you are using
Run in a terminal window:> dpkg -l hplip
[http://hplip.sourceforge.net/install/installtree.html#debian](http://hplip.sourceforge.net/install/installtree.html#debian)

that printer uses min.HPLIP version 2.7.6
[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

---

### Post by Uncle_Grombor on 2007-09-03
> **dreamyseahorse said:**
> Hello-

I have Feisty Fawn (7.04) and Windows Vista on my computer. My HP Photosmart C4240 All-In-One printer works fine in Windows but I tried to add the printer on Ubuntu and even though it recognized it I couldn't find it in the list. It might be a stupid question but I have looked everywhere and can't find if I should sign up for Photosmart C4100 (the closest listed as an option) or if I should install some kind of file to make it compatible. Any suggestions?

Under the list of HP model numbers is the name of the driver.  If you choose C4100, it should say that the recommended driver is hpijs.  This is the one that I have installed and the Printing and USB memory slots work fine.  I now have another question.  I cannot get the scanner to work.  I've looked through HP's website for information, I've checked out sane and didn't find this model of multifunction printer listed, nor was it listed in Ubuntu's help archive that I could find as a compatible device.  Thanks all and have a great holiday weekend.

---

### Post by linuxwizard on 2007-09-03
Uncle_Grombor
You are not going to get all features of the HP Photosmart C4240  till you are using min.HPLIP version 2.7.6 look at my post above. And you also need to install Sane.


[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)
Bottom of page.
3.  Scan supported means that PC initiated scan using a SANE compatible software application is supported over parallel, USB, or network (depending on I/O connection).

I think Feisty is using HPLIP version 1.7.3. So for that printer to work correctly you will have to update to newer version. The above post shows how. Than when you go to add that printer it will show in list.

---

### Post by Uncle_Grombor on 2007-09-04
Thanks.  I should have read the post a little closer.  Everything is up and running better then I ever thought possible.  As good as any printer in a windows enviornment.  Thanks again.

---

### Post by webmaker02 on 2008-03-05
I just bought an HP Photosmart c4240 printer/copier/scanner and can't get it to install on my Mac.  I'm running OSX 10.4, but it doesn't seem to recognize the printer.  Does anybody know how to get the printer to install?

Thanks,

J.D.

---

### Post by boeing777 on 2008-03-05
strangely, I have a HP Photosmart C4280, i just plug in the usb line and it works without any configuration.

---

