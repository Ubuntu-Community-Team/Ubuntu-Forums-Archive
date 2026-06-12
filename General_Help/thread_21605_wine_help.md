---
title: "wine help"
date: 2005-03-23
forum: General Help
---

### Post by t3rm1n8r1x on 2005-03-23
I've got wine installed on my computer, but i can't figure out how to set it up so that it sets drive c: to the windows partition on /dev/hda1, and winetools wants me to create a fake windows drive
the packages i downloaded are from the wine site:
wine_0.0.20050310-1_i386.deb
wine-dev_0.0.20050310-1_i386.deb(unneccesary?)
winetools_2.1.1-1_all.deb

can somebody tell me how/where to edit the configuration so that wine sees c: the way i want it to?

---

### Post by az on 2005-03-23
5.5. If I want to use a Windows install, which versions are OK?

Either use a classic no-windows install (Wine is getting better all the time) or use a Win9x install (Win95, 98, 98SE, ME). DON'T configure Wine to use an NT-based Windows install (NT, Win2K, WinXP, Win2K3).

In general, most Windows installations contain vast quantities of garbage that can confuse Wine and make it less reliable. If you can, it's best to install the programs you want into Wine's fake windows drive. 


I think winetools is a transitional project for the wine configurator.  It would seem that all of the stuff you can do with winetools (install and run IE6) would porbably not work in a real winodws setup.  Anyway, I would not try.

[http://www.winehq.com/site/howto](http://www.winehq.com/site/howto)
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

Have you tried to modify the .wine file by hand using winetools?

---

