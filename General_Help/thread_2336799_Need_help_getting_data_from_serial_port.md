---
title: "Need help getting data from serial port"
date: 2016-09-11
forum: General Help
---

### Post by DrScum on 2016-09-11
I have a device which sends printer data to a serial port, if a printer is connected the data are printed. I would like to collect the file and either create a pdf or access the data for further processing.
I have connected a serial port to usb adapter (I don't have a computer with serial port available) and the device is recognized as I found out using 
dmesg | grep tty 
as described here [https://help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom)

I couldn't get any data from the device however using the procedures described in the minicom post above. 
Thus my question: is there another application like minicom able to control serial communication? As I said, I am interested in at least getting a printout, being able to access the data for further processing would be even better of course.

---

### Post by oldfred on 2016-09-11
At least 15 or 20 years ago we used Windows & Zebra printers. Using Basic to send label info to print with ZPL code. We then wanted no printer driver adding its own codes. More like the very old DOS serial port days where we sent Epson escape codes to print bold or italics. Code was in software and there was no printer driver.

In Linux it is a raw print device which just passes data to port. I have not used it as now retired, and we never used Linux with ZPL. But I have saved a few links. Not even sure links are still valid.
Zebra & raw print device:
[http://code.google.com/p/jzebra/](http://code.google.com/p/jzebra/)
[http://qzindustries.com/download](http://qzindustries.com/download)
[http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu](http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu)
[http://qzindustries.com/TutorialRawUbuntu](http://qzindustries.com/TutorialRawUbuntu)

---

### Post by DrScum on 2016-09-12
Thanks for the reply. I tried the links and was able to install a raw printer but that didn't help me getting the data from the device.

I also installed minicom and apparently do get some data from the device (line of question marks and numbers changing in the terminal window) when I initialize a file transfer from the device.

I also tried various cat commands like cat /dev/ttyUSB0 but didn't get any data on the screen that way.

So I am still looking for some kind of application to be able to communicate with my device.

---

