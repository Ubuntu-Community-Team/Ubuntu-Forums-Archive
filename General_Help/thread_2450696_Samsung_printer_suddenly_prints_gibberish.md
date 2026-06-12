---
title: "Samsung printer suddenly prints gibberish"
date: 2020-09-18
forum: General Help
---

### Post by dora5 on 2020-09-18
I'm running Ubuntu 18.04, and a Samsung M270 printer.   I am using the drivers for that printer downloaded from the Samsung web site.

I was printing letters.  One printed perfectly.  The other printed in gibberish.   The original one now prints in gibberish too.

By gibberish I mean endless pages each with a row of rectangles at the top.

I tried uninstalling the printers and reinstalling them, redownloading the driver, and reinstalling it.

It's still printing in gibberish.

How do I fix it?

Yours,
Dora

---

### Post by MoebusNet on 2020-09-19
Since no-one else has had any input, I'll try to share what little I know. First, it appears that you have been doing what Ubuntu documentation suggests for Samsung printers (other than use something else) which is to use the manufacturers drivers. Since that was working an no longer does, it would appear something has changed - maybe an update? One thing you could try is booting from a previous kernel to see if that changes things: [https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version) 

If that doesn't work for you, you might have to use CUPS (Common Unix Printing System): [https://helpdeskgeek.com/linux-tips/how-to-install-almost-any-printer-on-ubuntu/](https://helpdeskgeek.com/linux-tips/how-to-install-almost-any-printer-on-ubuntu/) 

I had to do this for an antique Samsung laser printer (it still had a parallel port!).

---

### Post by TheFu on 2020-09-19
Bad usb connection or cable?  reseat both sides?
I have a samsung laser printer that has been working since 2006-ish, but it gets used for less than 200 pgs a year.

---

### Post by kurt18947 on 2020-09-19
I have a Samsung Xpress 2870(?) that will print gibberish - one or two lines of random characters per page and will continue until the paper is exhausted if I use "driverless" printing. The latest driver from HP's support site works as expected so far. That is not working for you but my Samsung also 'speaks' PCL5 I think, so some sort of LaserJet emulation. Maybe try that?

---

