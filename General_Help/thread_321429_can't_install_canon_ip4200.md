---
title: "can't install canon ip4200"
date: 2006-12-18
forum: General Help
---

### Post by zetetic on 2006-12-18
I followed this HowTo in order to install my Canon Pixma iP4200 printer:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200)

 But in point 9, when I select the file "usr/share/cups/model/canonip4200.ppd"", the installer gives me the following error:

«The PPD
/usr/share/cups/model/canonip4200.ppd
is already installed»

Offcourse it is not installed and I can't make it appear on the list either.

So I can't install the driver for the Canon iP4200 printer. Any hints why this is happening? I can't work without a printer...

zetetic

---

### Post by hanzomon4 on 2006-12-19
Pick cannon under the manufacture tab and iP4200 Ver.2.60 as the model, then click the driver tab to see if it's there already

---

### Post by zetetic on 2006-12-19
Thanks for your reply hanzomon4.

quote:
Pick cannon under the manufacture tab and iP4200 Ver.2.60 as the model, then click the driver tab to see if it's there already.

Unfortunately that model doesn't show up in any tab or list.

zetetic

---

### Post by hanzomon4 on 2006-12-19
I'll look around for some help and get back with you......

---

### Post by hanzomon4 on 2006-12-19
I can't find anything but that howto, have you tried going to the cannon website?

---

### Post by zetetic on 2006-12-19
Thanks for your replies hanzomon4.

I was getting the same error both on Ubuntu Dapper and Debian Etch.

I think there's something wrong with gnome-cups-manager.

I installed footmatic-gui, and with footmatic-gui I finally was able to select the file /usr/share/cups/model/canonip4200.ppd

Now the printer works flawlessy, on both systems. :)

I only have onde issue: in debian etch I can't perform maintenance tasks such us cleanning printer heads, cause the driver for debian doesn't allow that (as far as I know).

zetetic

---

### Post by hanzomon4 on 2006-12-20
Great!! I remember how frustrating it was when I first tried setting up a printer.....

---

### Post by tom76 on 2007-01-01
> **zetetic said:**
> Thanks for your replies hanzomon4.

I was getting the same error both on Ubuntu Dapper and Debian Etch.

I think there's something wrong with gnome-cups-manager.

I installed footmatic-gui, and with footmatic-gui I finally was able to select the file /usr/share/cups/model/canonip4200.ppd

Now the printer works flawlessy, on both systems. :)

I only have onde issue: in debian etch I can't perform maintenance tasks such us cleanning printer heads, cause the driver for debian doesn't allow that (as far as I know).

zetetic

There are some clues here:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200)

---

### Post by tom76 on 2007-01-01
Please register your interest in future Canon drivers for Linux:

[http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225#1](http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225#1)

---

### Post by zetetic on 2007-01-04
tom76: Thank you for your reply.

I was able to solve the problem in Debian by simply copying the /etc/cups directory from the Ubuntu installation into the Debian installation.

After that, I finally was able to install the canon drivers refered in the document posted on [https://help.ubuntu.com/community/Ha...nonPixmaIP4200](https://help.ubuntu.com/community/Ha...nonPixmaIP4200).

And with those drivers installed, I can now perform maintenance tasks (such us cleanning printer heads) in Debian etch also,

cheers,
zetetic

---

