---
title: "Canon PIXMA MG2520 Printer"
date: 2014-03-20
forum: General Help
---

### Post by Tristan_Williams on 2014-03-20
I have went through this once before, but I can't remember what I did to fix it.
I am running Xubuntu 13.10 32-bit.

I have a Canon PIXMA MG2520, and it is recognized as a printer on the "printers" application.

I cannot find any drivers for this printer.
None of the threads I found were of any help. These are the places I checked for results:
[http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg2520](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg2520)
[http://ubuntuforums.org/showthread.php?t=2204685](http://ubuntuforums.org/showthread.php?t=2204685)
[http://askubuntu.com/questions/418002/i-cant-install-canon-pixma-mg2520-printer-with-ubuntu-12-04lts-64bit](http://askubuntu.com/questions/418002/i-cant-install-canon-pixma-mg2520-printer-with-ubuntu-12-04lts-64bit)

Any ideas on how to fix it?

---

### Post by Tristan_Williams on 2014-03-21
Problem Solved.

Under the "Choose Driver" menu, when setting up the printer, you need to select a completely different devices driver.

Look for "PIXMA iP2700"

Select that as your driver instead of the one for PIXMA MG2520 (because there isn't one for MG2520)

---

### Post by pdc on 2014-03-22
Hi Tristan; I missed this thread

Canon **DO** provide drivers ............. in .deb and .rpm format; (and source code); and in both 32 and 64bit formats; with an install script in each to run ............ 

go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100550201.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550201.html)

to get the debian package; cnijfilter-mg2500series-4.00-1-deb.tar.gz

install through a terminal by downloading and saving and then

cd Downloads
tar -zxvf cnijfilter-mg2500series-4.00-1-deb.tar.gz
cd cnijfilter-mg2500series-4.00-1-deb
./install.sh

_____________________________--

Canon also supply a programme ScanGearMP to run the scanner

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100551901.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100551901.html) to download scangearmp-mg2500series-2.20-1-deb.tar.gz and close the terminal from above; reopen and then 
cd Downloads
tar -zxvf scangearmp-mg2500series-2.20-1-deb.tar.gz
cd scangearmp-mg2500series-2.20-1-deb
./install.sh

run ScanGearMP with 

> [COLOR="#FF0000"]scangearmp[/COLOR]

---

### Post by Sanctimonious_Ape on 2014-08-25
They really need a "Thanks" button here as I have seen in other forums.  You've certainly got mine, pdc!

---

### Post by pdc on 2014-08-26
glad you got the drivers installed! thanks for the thanks; enjoy the printer

---

