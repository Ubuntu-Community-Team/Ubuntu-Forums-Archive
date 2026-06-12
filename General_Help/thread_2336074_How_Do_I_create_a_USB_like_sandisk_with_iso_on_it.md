---
title: "How Do I create a USB like sandisk with iso on it"
date: 2016-09-04
forum: General Help
---

### Post by sam-c on 2016-09-04
How Do I create a USB like sandisk with iso on it:confused:

---

### Post by ajgreeny on 2016-09-04
Scroll down to see the **Easy ways to switch to Ubuntu** section of [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and it tells you how from Ubuntu, Windows or Mac.

---

### Post by oldos2er on 2016-09-04
> **sam-c said:**
> How Do I create a USB like sandisk with iso on it:confused:

Do you mean a bootable USB drive? I like [mkusb]("https://help.ubuntu.com/community/mkusb").

---

### Post by RobGoss on 2016-09-04
What are you using for your current desktop? This will help us recommend what's needed to create the USB with the ISO file on it

---

### Post by HermanAB on 2016-09-04
Note that lots of information on the interweb is just plain wrong.  Since many years, the Ubuntu ISO files are dual mode and will boot on both an optical disk and a USB schtick, without the need for any special preparation software. 

All that you need to do, is copy the ISO file byte for byte to the USB device.  You can do that on Winders with rawrite or on Linux/Mac with dd (or even with cat).

---

### Post by sam-c on 2016-09-07
problem solved with cp to sandisk:D

---

