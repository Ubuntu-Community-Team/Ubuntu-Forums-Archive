---
title: "Skype camera for Ubuntu 12.04 to old and not available"
date: 2012-12-22
forum: General Help
---

### Post by lumaja on 2012-12-22
After spending 4 days to find all about Skype and cameras for Ubuntu 12.04 found
 that a camera for this Ubuntu is to old and is  not for sale any more.
 I want to complete escape from Windows but having family at other country I have
 to restart windows.   
 Is there someone can give advise  how to overcome this or methods to go around this PLEASE.

---

### Post by mörgæs on 2012-12-22
With which camera are we dealing?

---

### Post by netgooroo on 2012-12-22
I have skype on my laptop and, I am using 12.04 as wll and, I have not had any issues with Skype recognizing my cam. 

Does Ubuntu itself see your cam when it is plugged in? I know I have had some issues with certain peripherals working "out of the box" in the past with Ubuntu. However, for the most part, most things are "plug n play" these days. 

If your cam is an older one, you may have to upgrade. Never fear though as there are inexpensive cams you can find online that will work just fine.

---

### Post by NikTh on 2012-12-22
Except from Skype .. also there is Googletalk .. hangout via google account.. just in case you didn't know. 

As for Skype , please give more info about the camera. 

Plug in ,  open a terminal(CTRL+ALT+T) and give here the results of this command 
```
lsusb
``` 

Also you can test if your camera works in Ubuntu , maybe this is a Skype's specific problem. 
Form terminal again ```
gstreamer-properties
``` ,at the opened window click on **"Video" **and **"Test"** at **Default Input** .. and see if camera works. 
If not , then give here the results from terminal.. 
Thanks

---

### Post by lumaja on 2012-12-23
Thank you to answer to this problem.
 Explaining my problem and some history
 Camera Logytech QuickCam 8.4.8 or MacOS QuickCam 8.0.1.
 Install Skype from Software Center and register to Skype.
 Made test connect to family overseas but they cant see me (no camera)
 Install Cheese and guvcview checking in Synaptic notice it had to be upgrade to "Skype 4.1.0.2.0-Obuntu0.12.04.2 and Skype-bin", I did the upgrade and test camera with cheese, the picture keeps  
 going off on and decide to research in “Ubuntu Documentation Skypewebcams” found camera for Ubuntu 12.04.
 

                                                Logitech [QuickCam]("https://wiki.ubuntu.com/QuickCam")             Chat              
                               12.04 32-bit
                               046d:092c              
                               gspca_main              
                As my camera is not Chat it confirm my suspicion camera was to old.
 I decide to get another, which is Logitech Webcam C110. After connecting to family they cant see the camera .
 Following your advise results first the Old camera QuikCam 8.4.8.
 TEST lsusb
 

 luis@luis-G41M-Combo:~$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 002: ID 046d:092c Logitech, Inc. QuickCam Chat  
 luis@luis-G41M-Combo:~$  
 

 luis@luis-G41M-Combo:~$ gstreamer-properties  
 

 (gstreamer-properties:2775): Gtk-WARNING **: Unknown property: GtkDialog.has-separator  
 

 (gstreamer-properties:2775): Gtk-WARNING **: Unknown property: GtkDialog.has-separator  
 gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'  
 gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'  
 gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'  
 gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'  
 gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'  
 gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'  
 gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'  
 gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'  
 gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'  
 gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'  
 luis@luis-G41M-Combo:~$
 

 

 ON TEST  camera flashes on and off like running in Cheese.
 

 Second camera Logitech Webcam C110.
 luis@luis-G41M-Combo:~$ lsusb 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 003: ID 046d:082b Logitech, Inc.  
 luis@luis-G41M-Combo:~$  
 luis@luis-G41M-Combo:~$ gstreamer-properties 
  
 (gstreamer-properties:2461): Gtk-WARNING **: Unknown property: GtkDialog.has-separator 
  
 (gstreamer-properties:2461): Gtk-WARNING **: Unknown property: GtkDialog.has-separator 
 gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink' 
 gstreamer-properties-Message: Skipping unavailable plugin 'esdsink' 
 gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink' 
 gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink' 
 gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink' 
 gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc' 
 gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc' 
 gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc' 
 gstreamer-properties-Message: Skipping unavailable plugin 'esdmon' 
 gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc' 
 luis@luis-G41M-Combo:~$  
 

 ON TEST  camera working perfect.
 I will very gratefully to fix this

---

### Post by mörgæs on 2012-12-30
Does this help?

[http://ubuntuforums.org/showthread.php?t=1984328](http://ubuntuforums.org/showthread.php?t=1984328)

---

