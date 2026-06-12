---
title: "Terapin Mine - USB driver"
date: 2007-06-28
forum: General Help
---

### Post by saabsista on 2007-06-28
Hello everybody,
I own an Acer Travelmate 2501LMi laptop, and a Terapin Mine ([http://www.linuxdevices.com/articles/AT7443334424.html](http://www.linuxdevices.com/articles/AT7443334424.html)). 
They can't communicate via USB, so I can't download the audio files I recorded with the Mine on my laptop.

The Mine comes with a floppy disk  that contains some files

The readme.txt says:

> This diskette contains :

1) USB Driver for Win 98
You can connect mine to any Windows 98, Windows 2000 or Windows ME PC with the supplied industry standard USB cable.
If you are using Windows 98 standard edition, PC will require this device driver for the first time installation.  Please refer to the Installation Guide (Installation Guide.doc or Installation Guide.pdf).

2) USB Driver for mineBoot.
mine has a firmware recovery system that allows you to repair damages to mine's firmware caused by illegal shutdwn.
mine's firmware recovery can also be used to upgrade new firmware that are available on mine Information Services. You should constantly check [www.mineterapin.com](www.mineterapin.com) for the availibility of such upgrades.
PC will require this device driver for the first time installation.  Please refer to the Installation Guide (Installation Guide.doc or Installation Guide.pdf).

The others are:
the installation guide, that describes how the driver installation wizard works
an .exe file, the software recovery application
three files .inf, .sys and .pdr
a directory USB Driver For Mine Boot that contains an .inf file and a .sys one
a directory USB Driver For Win 98 that contains an .inf file, a .sys and a .pdr one

I tried Wine with the .inf .sys and .pdr files. but it doesn't work

I guess the driver is the .inf file

Anybody has a suggestion about how to install this driver in feisty?

thanks a lot
ciao

---

