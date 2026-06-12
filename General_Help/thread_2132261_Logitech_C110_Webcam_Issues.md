---
title: "Logitech C110 Webcam Issues"
date: 2013-04-04
forum: General Help
---

### Post by codeanticode on 2013-04-04
I recently tried out some screen capture software (recordmydesktop), but I wasn't really thrilled with it. After uninstalling it my Logitech C110 cam no longer works. It was fine before, but now I can't get it to work with Skype, Cheese, Empathy, or anything else, regardless of how I play with the settings. The cam turns on just fine, but all I get is a black screen. The cam is recognized when I run lsusb, but when I do lsusb -d 046d:0829 -v | grep "14 Video" I get: 

> 
can't get device qualifier: Operation not permittedcan't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
      bFunctionClass         14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video


I tried updating my UVC drivers, but I haven't had any luck. I know the cam works, as I've had no problems before, but I'm completely stumped as to why it stopped working. I'm running 10.04, and while I'm pretty green when it comes to Linux, I've tried pretty much everything I can think of with no results. Any ideas?

---

