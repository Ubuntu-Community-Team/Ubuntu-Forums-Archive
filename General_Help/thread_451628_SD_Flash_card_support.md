---
title: "SD Flash card support"
date: 2007-05-22
forum: General Help
---

### Post by Eagleon on 2007-05-22
Hi Everyone,

Back when I had windows, my SD Flash card slot was detected by the OS and I could read the memory card from  a folder in "My Computer". I was wondering how I could get my flash card reader to work on ubuntu. Its attached to my laptop so what I want is for the folder to pop up as if I had plugged in a usb flash drive. I am taking about the memory cards used for digital cameras. Any help will be greatly appriciated....

Thank you so much,
Eagleon..

P.S. Laptop is Toshiba M400 Portege Tablet

---

### Post by blazercist on 2007-05-22
well in theory it should automagically popup on your desktop... are you sure that the reader is recognized properly?  I have no experience with flash cards but try typing "lsusb" in console and paste the output here.

---

### Post by Eagleon on 2007-05-22
Hi, thanks a lot! here is the output from lsusb

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0053 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by blazercist on 2007-05-22
hmm unless your SD Card reader is made by MS, then I think that I have found your problem, the device hasnt been deteced.... try searching google to see if theres a linux driver for that particular reader. if not you may need to invest a couple dollars and get yourself a linux compatible one.

one second wait, is this thing built in or like a usb attachment? perhaps i misunderstood.

---

### Post by Eagleon on 2007-05-22
hi, thanks again...

yeah, sadly the darn thing is built in to the laptop. there is a little slot on the right side of the computer where I can slide in my SD cards. The laptop is a Toshiba Portege M400... I don't think there are any drivers avaliable for it though :( where should I look? i tried Google.. not much luck!

thanks

---

### Post by blazercist on 2007-05-23
nah i think ur beat, just buy a usb one for like 10 dollars.

---

### Post by Eagleon on 2007-05-24
oh well... :( I really wanted to use this one! 

Anyways, what about that fingerprint scanner? any chance I could get that working with ubuntu by any chance? thanks..

---

### Post by Eagleon on 2007-05-25
any ideas anyone? :(

---

### Post by cjramsey22 on 2007-12-24
It's the M405 but it should work.

[http://www.math.upenn.edu/~vincentb/UbuntuPortege.html](http://www.math.upenn.edu/~vincentb/UbuntuPortege.html)

Hope it helps.

ramsey

---

### Post by fragos on 2007-12-24
On desktops all card readers are USB as are many other external devices.  On laptops this may not be the case.  To keep cost down and power requirements low many laptops use proprietary hardware for card readers.  Without documentation on the hardware open source developers have a difficult time creating divers.  It was true USB there would be no problems in Linux.

---

