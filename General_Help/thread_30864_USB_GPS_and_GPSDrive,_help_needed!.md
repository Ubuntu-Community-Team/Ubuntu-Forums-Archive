---
title: "USB GPS and GPSDrive, help needed!"
date: 2005-04-30
forum: General Help
---

### Post by tkz on 2005-04-30
Hi,

For a couple of days now, I've tried to get position information from a GPS to GPSDrive program. I use a laptop that has no serial port, only USB port. When I type lsusb in the shell, it seems that the laptop correctly sees the Garmin GPS but still I have no idea how to configure GPSDrive to receive information from the device. There is no /dev/ttyUSB0 or anything like that on my machine.

Any pointers?

tk


 ](*,)

---

### Post by gw90se on 2005-06-25
I was just over on gpsdrive's website and saw a mention of a fix for the garmin and usb. Do a google search and find their pages then look under the FAQ's

 :roll:  OOPS!!, my bad, that was on the gpsbabel site, but it may still offer you a clue to your fix.

---

### Post by MrSandman on 2005-07-04
I can verify that raw gps data can be captured on a USB port under Linux with the earthmate.


root@ubuntu:/home/sandman # emul_test
Device successfuly opened.
$PSTMVER,GPS Version 4.20.5 Release ARM (15:52:14 Feb 4 2005),0x8C0B
$GPRMC,033324.000,V,3800.946,N,08734.142,W,0.0,0.0,040705,2.4,W*75
$GPGGA,033324.000,3800.94640,N,08734.14171,W,0,00,99.0,121.07,M,-33.1,M,,*6D
$GPVTG,0.0,T,357.6,M,0.0,N,0.0,K*49
$GPGSV,3,1,10,03,11,049,00,07,14,229,00,08,66,313,00,11,42,129,00*7A
$GPGSV,3,2,10,13,15,196,00,19,39,046,00,27,78,171,00,28,39,293,00*74
$GPGSV,3,3,10,29,13,319,00,31,33,230,00,,,,,,,,*79

---

