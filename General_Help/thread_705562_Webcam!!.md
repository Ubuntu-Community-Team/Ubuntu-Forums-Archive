---
title: "Webcam!!"
date: 2008-02-23
forum: General Help
---

### Post by skylinedna on 2008-02-23
Can anyone tell me how to get cheese or camorama to pick up my webcam? device manager has registered it. its a intergrated camera but run through usb 2.0 somehow. made by sonix device manager says. i got all information if anyone needs it thanks

---

### Post by linuxwizard on 2008-02-23
Try using Ekiga to see if cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. If it does not work > post results of the command > lsusb

---

### Post by skylinedna on 2008-02-23
skylinedna@skylinedna:~$ lsusb
Bus 005 Device 002: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

i dont really know what im doing enough to change settings but ill give it a go heres the results of that though dude

---

### Post by linuxwizard on 2008-02-23
Bus 005 Device 002: ID 0c45:62c0 Microdia > webcam

For Microdia webcams you can look here for the driver > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by skylinedna on 2008-02-23
well it says it picks up the camera but no picture shows up....

---

### Post by skylinedna on 2008-02-23
oh k i installed that driver or a generic one. how do i manually set up with rebooting. sorry to be difficult but i would like to learn

---

### Post by linuxwizard on 2008-02-23
Is their a orange moving globe or a black screen ? If black screen try working with the settings ? When you open Ekiga a long the bottom you will see 3 tabs Dialpad, Audio, Video, click on video you can make adjustment there also.

---

### Post by skylinedna on 2008-02-23
orange globe mate.....

---

### Post by linuxwizard on 2008-02-23
> skylinedna  	
Re: Webcam!!
well it says it picks up the camera but no picture shows up....

My last post was for to help with no picture. I didn't plan on you going a head and installing the driver. Did you check and see if that driver supports your webcam ? I don't know anything on that driver just know that it is used for Microdia webcams.

---

