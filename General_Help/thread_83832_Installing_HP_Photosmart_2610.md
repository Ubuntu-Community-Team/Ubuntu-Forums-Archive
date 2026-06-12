---
title: "Installing HP Photosmart 2610"
date: 2005-10-29
forum: General Help
---

### Post by prsmith on 2005-10-29
Help!

I am new to Linux and have installed Kubuntu 5.10

I have a new HP Photosmart 2610 All-In-One printer-scanner-copier-fax which I can not print to from Kubuntu.

Does anyone else have this device installed?  Can someone tell me how to install it?

Thanks

Preston

---

### Post by prsmith on 2005-10-29
I forgot to mention that this is a network printer on my home LAN

I finally got it to pint using the HP 2600 drivers but now the scan/OCR function is not operating.  So my question this time, is how do I get the scanner working.  Kooka does not see it and I can not install it

Thanks
Preston


[QUOTE=prsmith]Help!

I am new to Linux and have installed Kubuntu 5.10

I have a new HP Photosmart 2610 All-In-One printer-scanner-copier-fax which I can not print to from Kubuntu.

Does anyone else have this device installed?  Can someone tell me how to install it?

Thanks

Preston[/QUOTE]

---

### Post by AmiraHime on 2005-11-13
Ah!  I have the same problem with my HP Photosmart 2610, and I have the unfortunate problem of being a total newbie when it comes to Linux OS.

I am in dire need of help! I Linux Drivers for this particular writer, and HP does not offer you any.

---

### Post by andrebtoda on 2006-09-01
I have the same problem!!!
HELP ME PLEASE!!!!

---

### Post by volition on 2006-09-19
Andre,

It's a fairly simple process with HP printers:

1) Find out the LAN ip address for your HP 2610 (in this example let's use 192.168.1.70)

2) Open a console and type the following:

**hp-makeuri 192.168.1.70**

3) The system should return something like this:

 HP Linux Imaging and Printing System (ver. 0.9.7)
 Device URI Creation Utility ver. 2.5

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 Creating URIs for '192.168.1.70':
CUPS URI: hp:/net/Photosmart_2600_series?ip=192.168.1.70
SANE URI: hpaio:/net/Photosmart_2600_series?ip=192.168.1.70

4) To use xsane, goto **Applications -> Accessories -> Alacarte Menu Editor**

5) Select **Graphic** and **Xsane**

6) Right click on **Xsane** and select **Properties**

7) Change **command** to **xsane hpaio:/net/Photosmart_2600_series?ip=192.168.1.70**

That's it done, you can now restart xsane and it will start using the HP 2610 scanner.

Remember to change the IP address to your own.

Gus.

---

### Post by kryliss on 2007-12-16
Thanks for the info. This worked for me using Kubuntu 7.10

---

### Post by bwakkie on 2008-07-12
So what do you do when you only use usb access?

---

