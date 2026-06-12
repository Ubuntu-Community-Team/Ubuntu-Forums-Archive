---
title: "GPSDrive and Delorme Earthmate GPS"
date: 2008-04-16
forum: General Help
---

### Post by dangoeslinux on 2008-04-16
I have an older original Delorme Earthmate GPS receiver. It seems it works under Ubuntu. If I plug it in I can see the GPS raw data in the terminal (see below):

laptop:~$ cat /dev/ttyUSB0
*.00,0.00,160408,,*19
$Version 231.000.000ES-01501
$GPS Port B : User Protocol
$TOW: 337069  
$WK:  1475
$POS: 1009392  -4465473 4426100 
$CLK: 91576   
$CHNL:12

$Baud rate: 4800  System clock: 24.553MHz
$HW Type: S2AM
$Asic Version: 0x23
$Clock Source: GPSCLK
$Internal Beacon: None
$LED Flash rate : OnTime: 10 , OffTime: 10
$GPGGA,214630.000,4413.4997,N,07715.7627,W,0,00,50.0,84.5,M,-34.9,M,0.0,0000*4D
$GPGSA,A,1,,,,,,,,,,,,,50.0,50.0,50.0*05
$GPGSV,3,1,12,25,76,049,00,14,73,026,,32,59,299,,22,52,159,*73
......

I have GPSD and GPSDrive installed but somehow I cannot get it working in GPSDrive. I set the settings under preferences as follows:
- GPS is Earthmate - CHECK
- Interface: /dev/ttyUSB0
- Baudrate: 4800

If I click the Start GPSD button, the status bar shows for a second "No GPS used" and then it goes back to Simulation Mode.

Is there something I am missing? I read all related posts but I could not find any hint what to do next.

Thank you!

---

### Post by dangoeslinux on 2008-04-23
gpsd -p /dev/ttyUSB0 -S 2947 -N -D 5
fixed it in case somebody has the same problem.

gpsd -D 5 -nN /dev/ttyUSB0
works also.

---

