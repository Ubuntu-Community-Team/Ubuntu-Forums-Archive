---
title: "Libre Offfice writer freezes O.S. when copying text"
date: 2016-07-22
forum: General Help
---

### Post by John_Carver on 2016-07-22
Time after time using the mouse to highlight and then copy text, the program and system freeze and must reboot.

Thoughts??

---

### Post by him610 on 2016-07-22
Hopefully, one of the system "guru" moderators will jump in on this, because I am on unsteady ground here.

When you copy text with the mouse, it gets stored in a section of memory. When you perform the paste operation, it does not empty that section of  space, but it is free to be reused. 

If after performing a copy & paste operation, you find it necessary to reboot the system, it may indicate a defective memory module. At next boot, from the Grub Menu, select Memtest86+ to test the memory.

It may also be related to total/used/free/available memory, and how many applications are executing.

---

### Post by QIII on 2016-07-22
Hello!

It would be very helpful if you would post your machine's specs, the release of Ubuntu you are using and the version of LibreOffice.

---

### Post by grahammechanical on 2016-07-22
Do you have an Nvidia graphic adapter & are you using Nouveau the open source video driver? I used to get this almost a year ago with Libreoffice 5. It was GPU lockup and seen from the system messages when opening tty1 (Crtl+Alt+F1)

One solution is to switch to the proprietary video driver. I also found that large documents took a very long time to load. But things have improved for Libreoffice 5.1.4.2 that I am using in Ubuntu 16.04.

Regards.

---

### Post by John_Carver on 2016-07-23
Specs:
ASRock A780 GXE/128m
Platform i686
Ubuntu 14.04 Trusty
Unity 
Mem 3.9M
AMD Athlon 64x2 Dual Core Processor 6000+
Libre Office:  Version: 4.2.8.2
Build ID: 420m0(Build:2)

---

### Post by smelheim85 on 2016-07-24
Have you updated the graphics card on your board by chance?  Your most likely using a stock Raedon graphics card.  Any chance you could run 

```
lspci -v | grep VGA
```

---

### Post by John_Carver on 2016-07-26
No such file or directory

---

### Post by smelheim85 on 2016-07-27
So when you type

```
 lspci -v | grep VGA 
```

you say that the terminal gives you error message "No such file or directory"?

---

### Post by John_Carver on 2016-07-28
yes

---

### Post by smelheim85 on 2016-07-30
I've never had this happen to me before but I did find someone that did from other forums.  It appears that on some Debian based systems pciutils aren't installed by default. Try this then we try the lspci command;

```
 sudo apt-get install pciutils 
```

---

### Post by John_Carver on 2016-08-07
already installed

Already installed
I am going to install Ubuntu 16.04
Maybe that will fix it
Mem test was ok

---

### Post by vasa1 on 2016-08-08
You reported something similar way back in October 2014: [Libre Office freezes system]("https://ubuntuforums.org/showthread.php?t=2249660")> Ubuntu 14.04 Libre Office
I have had this application freeze the O.S. on numerous occasions when doing a copy of a document in order to try and paste it elsewhere.
There is no option to kill the application so it is necessary to restart and hope for a document recovery.
Anyone else experiencing this and have a soution

---

