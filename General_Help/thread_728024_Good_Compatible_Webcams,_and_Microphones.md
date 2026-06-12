---
title: "Good Compatible Webcams, and Microphones"
date: 2008-03-18
forum: General Help
---

### Post by mlyons16 on 2008-03-18
Hey everyone,

I've fallen for the Skype addiction and I need to get set up with the webcam, headset type thing... what are some good quality, not so expensive ones that are very compatible with Ubuntu?

---

### Post by mlyons16 on 2008-03-18
[http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/3056&cl=ca,en](http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/3056&cl=ca,en) 

I particularly like this webcam.

---

### Post by TeoBigusGeekus on 2008-03-18
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by mlyons16 on 2008-03-18
> **TeoBigusGeekus said:**
> [https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

Alright, well the out of the box functionality webcams, the Logitech Quickcam Pro 9000 is listed. So what do I do, just plug it in and away you go?

Most microphones would be compatible right? That's just using a basic microphone jack driver right?

I'm on 7.10 Ubuntu Gutsy and the skype is version: 2.0.0.63

---

### Post by TeoBigusGeekus on 2008-03-18
No mate, you need to install the uvcvideo driver
[http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")

---

### Post by mlyons16 on 2008-03-18
> Open a console and execute:

 apt-get install subversion

or open the tool synaptic and select subversion in the GUI.

Get the source code
Open a console and execute the following command:

 svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc 


I understand up to there, Then do I just continue to follow:

>  Install needed packages
You need to install a few packages (Please update list if you encounter problems due to missing packages)

Install the follwing packages with apt-get install ... or use Synaptic.

    * build-essential
    * kernel-headers
    * ...(I have a developer machine, so many packages were already present, please update this list) 

Compile Linux-UVC

   1. Enter the check-out Linux-UVC folder
      cd trunk
   2. Open the Make file in this directory
      sudo nano Makefile
   3. Edit Makefile to change the modules path from
      INSTALL_MOD_DIR := usb/media
      to
      INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo
   4. make
   5. sudo make install

---

### Post by TeoBigusGeekus on 2008-03-18
Try this thread
[http://ubuntuforums.org/showthread.php?t=241681]("http://ubuntuforums.org/showthread.php?t=241681")

---

