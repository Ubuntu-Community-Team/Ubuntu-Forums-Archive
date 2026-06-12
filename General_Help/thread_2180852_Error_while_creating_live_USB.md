---
title: "Error while creating live USB"
date: 2013-10-14
forum: General Help
---

### Post by Parks on 2013-10-14
I am trying to create a live USB with Startup Disk Creator, and i get an error: 
An uncaught exception was raised:
[Errno 5] Input/output error
I am using a 4gb usb drive and the iso is 13.04. 
I did this before with no issues, but now it seems something is wrong. I checked out[ this thread ]("http://ubuntuforums.org/showthread.php?t=1339463&page=2") but it seems that the user just was using a corruped cd. I made sure I had a fresh iso image and I have tried several diffrent usb drives. Any thoughts?

---

### Post by fantab on 2013-10-15
Try another tool, like Unetbootin:
*sudo apt-get install unetbootin*

Input/Output error generally means that there is something wrong wiht the USB... try another USB port to plugin your USB Disk.

---

### Post by sudodus on 2013-10-15
Welcome to the Ubuntu Forums :-)

I do not understand exactly what is happening for you. Please have a look at the following links, try again and report back with as much details as possible.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by philinux on 2013-10-15
> **Parks said:**
> I am trying to create a live USB with Startup Disk Creator, and i get an error: 
An uncaught exception was raised:
[Errno 5] Input/output error
I am using a 4gb usb drive and the iso is 13.04. 
I did this before with no issues, but now it seems something is wrong. I checked out[ this thread ]("http://ubuntuforums.org/showthread.php?t=1339463&page=2") but it seems that the user just was using a corruped cd. I made sure I had a fresh iso image and I have tried several diffrent usb drives. Any thoughts?

I would use the Disks utility from ubuntu and format the usb as fat32 first.

---

### Post by Parks on 2013-10-16
Thank you fantab, I used  Unetbootin and at first it did not work with the iso I had allready downloaded, but when I used the feature that imports the iso it worked perffectly. I think that what happend is that the version of the iso I was using was corupted. Thanks for the help

---

