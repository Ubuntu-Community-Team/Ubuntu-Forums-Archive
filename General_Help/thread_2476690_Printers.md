---
title: "Printers"
date: 2022-07-03
forum: General Help
---

### Post by jacksonguitars on 2022-07-03
Dear sirs and ladies!

I cant install this printer...
[https://support.hp.com/us-en/drivers/selfservice/hp-laser-100-printer-series/24494339/model/24494340](https://support.hp.com/us-en/drivers/selfservice/hp-laser-100-printer-series/24494339/model/24494340)

Is it compatible with Ubuntu 22.XX?

---

### Post by yancek on 2022-07-03
HP printers are generally known for compatibility with Linux.  When you tried to connect the printer, what happened?  You will need to provide specific information on any warning or error messages you got when you tried to install drivers.

---

### Post by jacksonguitars on 2022-07-03
Thank you, sir. Ubuntu installs the drivers without hesitation. But the Printer stays silent inserting the USB into the computer.

---

### Post by yancek on 2022-07-03
>  But the Printer stays silent inserting the USB into the computer. 		

Not sure what that means.  Are you attaching the printer to the computer with a USB cable?  What happens when you try to print a simple text file?  Have you gone to your Settings menu and configured or added it to the printer list?

---

### Post by Autodave on 2022-07-03
....and what drivers did you install?  I have never had to install a driver for an HP printer.

---

### Post by ajgreeny on 2022-07-03
The site you linked in your first post is for Windows drivers, nothing to do with Linux so you can forget that.

How is the printer connected, by wireless or USB cable as that is not clear and I also can not understand your comment ***"But the Printer stays silent inserting the USB into the computer. "***

Have you actually tried printing a page from, for example, Libreoffice?

Also see what the CUPS webmin page at ***[http://localhost:631/](http://localhost:631/)*** shows you in your web-browser; it should list printers connected if you click on Printers in the very top menu and allow you to administer them if you need to.

For some background and to see how well your printer is supported go to [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index) and search for the exact model.
I can not find a Laser 107a listed there at all

---

### Post by jacksonguitars on 2022-07-04
Thank you, sirs. The link to HP which I provided gives you an option to choose Linux as an OS and then Ubuntu. So, I installed the Ubuntu drivers. CUPS localhost:631 does not return anything printer-wise. So I'm throwing in the towel. To much work,

---

### Post by yancek on 2022-07-04
As I asked in my earlier post, did you go to Settings, Printers to Add your printer?  If so, what happened?  If not, you need to first do that.

Not sure from your last post what you typed in the browser but, all you need do to show the CUPS page is type the following in the browser address bar:  localhost:631

---

### Post by Autodave on 2022-07-04
You can throw in the towel if you wish, but an HP printer is the easiest of all of them to install.  I believe that you are making it way more difficult than it needs to be.  If you are ever planning on printing something, you had better get this printer working.  Anything else that you purchase will be a LOT harder than an HP.  

I have never had to do anything other than connect an HP printer, go into settings and choose it.  Even my wireless HP laser printer connected that way.......took almost 30 seconds of "setup" to have it printing the first time!

---

### Post by TheFu on 2022-07-04
The best answer for which printer to buy is one that uses driverless printing. This is a standard and removes any need for driver on clients.
[https://openprinting.github.io/driverless/](https://openprinting.github.io/driverless/)

In 20.04 and later, using almost any Ubuntu desktop DE, the printer should be magically discovered and configured. You might need 5 seconds to confirm the printer for the first use, but after that, it "just works."  Even in 16.04 and later, with the correct printers, there is a system-printer-config tool that only needed to choose 3 things
Vendor (HP/Brother/etc ...) ----> Printer Model (ml1740/mfc-240c) ---> Protocol to be used - always choose IPP, if possible.

I suppose some odd printers or printers that need proprietary drivers will be harder, but if you get the correct vendor and model printer, it really is plug -n- use for the last 8 yrs on Linux.  That includes many network printers too, provided avahi is running on your Ubuntu system.  I only buy USB connected printers, but then connect them to an Ubuntu system here that provides the IPP interface for all other devices in the building.

> **Autodave said:**
>  I have never had to do anything other than connect an HP printer, go into settings and choose it.  Even my wireless HP laser printer connected that way.......took almost 30 seconds of "setup" to have it printing the first time!

This has been my experience too, though I don't have any HP printers.

---

### Post by kurt18947 on 2022-07-04
> **jacksonguitars said:**
> Thank you, sirs. The link to HP which I provided gives you an option to choose Linux as an OS and then Ubuntu. So, I installed the Ubuntu drivers. CUPS localhost:631 does not return anything printer-wise. So I'm throwing in the towel. To much work,

I followed that link. It does point to a compressed file that looks at first glance like the installer for Samsung, there are several scripts once extracted. All this really shouldn't be necessary AFAIK. Has HP gone away from HP-LIP (however it's spelled)? This driver would need to be installed from a command line which can be intimidating for someone new.

---

### Post by mIk3_08 on 2022-07-05
> **jacksonguitars said:**
> Dear sirs and ladies!

I cant install this printer...
[https://support.hp.com/us-en/drivers/selfservice/hp-laser-100-printer-series/24494339/model/24494340](https://support.hp.com/us-en/drivers/selfservice/hp-laser-100-printer-series/24494339/model/24494340)

Is it compatible with Ubuntu 22.XX?
Yes. It is supported. Just configure it properly. Just try to install this driver for your Linux Ubuntu Operating System [Click here]("https://support.hp.com/us-en/drivers/selfservice/hp-laser-100-printer-series/24494339/model/24494340"). Regards and cheers.

---

