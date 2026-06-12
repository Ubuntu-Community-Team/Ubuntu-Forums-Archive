---
title: "USB/Serial interface cable to UV-5R XCVR"
date: 2018-06-26
forum: General Help
---

### Post by C.Snyder on 2018-06-26
Greetings,
                          
 [LEFT]**Platform:**  I5 Laptop running Ubuntu 14.04.  Prolific PL2303 USB to Serial programming cable.[/LEFT]
 [LEFT]In the past, I have been able to access the UV-5R radio's configuration.
[/LEFT]
 [LEFT]The laptop's OS is up to date as well as the Chirp Daily Builds (open source radio configuration program)
[/LEFT]
 [LEFT]**dmesg:**                            [/LEFT]
 [ 1900.825659] usb 3-2: new full-speed USB device number 3 using xhci_hcd  
  [ 1900.842467] usb 3-2: New USB device found, idVendor=067b, idProduct=2303  
  [ 1900.842475] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0  
  [ 1900.842480] usb 3-2: Product: USB-Serial Controller  
  [ 1900.842485] usb 3-2: Manufacturer: Prolific Technology Inc.  
  [ 1900.943247] usbcore: registered new interface driver usbserial  
  [ 1900.943264] usbcore: registered new interface driver usbserial_generic  
  [ 1900.943278] usbserial: USB Serial support registered for generic  
  [ 1900.967300] usbcore: registered new interface driver pl2303  
  [ 1900.967333] usbserial: USB Serial support registered for pl2303  
  [ 1900.967357] pl2303 3-2:1.0: pl2303 converter detected  
  [ 1900.968085] usb 3-2: pl2303 converter now attached to ttyUSB0
          #System sees the interface device#

 **Attempt to read radio's configuration:**

   [LEFT]                      [/LEFT]
 [LEFT]"Due to the fact that the manufacturer continues to release new versions of the firmware with obscure and hard-to-track changes, this driver may not work with your device. Thus far and to the best knowledge of the author, no UV-5R radios have been harmed by using CHIRP. However, proceed at your own risk!"[/LEFT]
 [LEFT]And then results in:[/LEFT]
 [LEFT]"could not open port /dev/ttyusb0: [Errno 2] No such file or directory: '/dev/ttyusb0"[/LEFT]
 [LEFT]**Question:**[/LEFT]
 [LEFT]Has this issue been seen by someone in the group and a could you share your insight?[/LEFT]
 [LEFT]I have  searched the Ubuntu Forums and do not find a mention of this specific  issue.  The closest thread involved an OS upgrade to 16.04 that required  an uninstall of the Chirp program/App and a reinstall.  Since I appear  to be dealing with a driver/dependency issue, I have not tried this  approach.

I have posted this text to the email forum at the Chirp / Danplanet web site as well.

Do any of the Forum members recognize the issue I am dealing with?
Could it be that the driver/dependency is not located in the same place in which the Program/App is operating?

73's
[/LEFT]

---

### Post by wildmanne39 on 2018-06-26
I have seen that error, all I had to do is change the port in the drop down menu of chirp, is your exact radio listed in chirp? No I do  not believe it is a driver issue.

---

### Post by HermanAB on 2018-06-26
Linux is case sensitive:
/dev/ttyUSB0

---

### Post by C.Snyder on 2018-06-29
Thank you both for responding to my post.
I received a reply form the Chirp email forum and such as **HermanAB** points out the case sensitivity was the issue.
I must admit to being numb to case compliance.  Most often, case is automatically interpreted in all but password functions.
Any yes **wildmanne39**, it was not as I suspected a driver issue.  
Now I am dealing with a permissions issue in the form of an "Errno13".  I have been doing some research in the Forum and will make another pass at the radio soon.
I use the UV-5R to monitor and in emergency situations, communicate with the local fire department.  Seeing as how the neighborhood (a small rural community in a pine forest) is in the middle of a extremely dry fire season the radio's function is important.
Your help with my DIY project is greatly appreciated.

73's

---

### Post by C.Snyder on 2018-07-01
After a lot of reading both outside and inside the Forum, I found this link
[https://ubuntuforums.org/showthread.php?t=2393916&highlight=permissions+Chirp](https://ubuntuforums.org/showthread.php?t=2393916&highlight=permissions+Chirp)
to a similar Chirp + radio issue.
I did not fully understand the syntax of the usermod apporach.
And with the help of Galen Thurber via the Chirp email forum;
> enter a command line
# sudo adduser USER_ACCOUNT_NAME dialout
enter your password
logout and back in again

With the case sensitive clue and the user account name added to the dialout group, I have been successful in accessing the radio's settings.
My thanks for the help.
73s

---

