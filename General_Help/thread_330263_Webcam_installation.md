---
title: "Webcam installation"
date: 2007-01-02
forum: General Help
---

### Post by moonliter on 2007-01-02
Please can you help me to solve problem:
I am trying to install usb webcamera Jetion but it don't work on ubuntu and also in winxp say just found new hardwer but can't find apropriate driver.Also when I click on ubuntu lsusb I got this: 
Bus 001 Device 003: ID 06a2:0003 Topro Technology, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

I also have installed camorama webcam viewer and easycam2 and in camorama when try to open says:Could not connect to video device (/dev/video0) Please check connection,and in easycam2 says no camera or no compatible camera found

please help!!!

---

### Post by fragos on 2007-01-03
What you need is an appropriate driver.  May I suggest you check [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) which worked for my Logitec and does support a large number of common chip sets.  I'm not familiar with the brand you have.  The developer has gone to a lot of trouble to insure the install is a single step operation.  There will be a shell script gspca_build that will do all you should need for installing and registering with your system for startup at every boot time.

---

### Post by satyam on 2007-01-16
Hi

Moonliter, I've got a camera that's also made by Topro. Unfortunately, I've had no luck getting it to work in Ubuntu. Yet. If you want drivers for another os, check this site:

[http://topro.com.tw](http://topro.com.tw)

Good luck.

---

