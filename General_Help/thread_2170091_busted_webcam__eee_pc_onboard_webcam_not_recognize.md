---
title: "busted webcam?  eee pc onboard webcam not recognized in xubuntu"
date: 2013-08-24
forum: General Help
---

### Post by casey4 on 2013-08-24
i'm casey.  i'm new to ubuntu, as will become obvious..


 I recently purchased an Asus Eee pc 1000H from ebay. The seller  installed Windows 7 (upgraded from XP) on it before selling it. When i  tried to use the camera, Skype couldn't find it. Neither could the  windows device manager. The seller says it worked with xp and might be  missing a driver. 
  

I also checked that Onboard Camera was set to "enabled" in the BIOS. 

  

I suspect that it is not a hardware issue, since it stopped working  after switching from XP. I installed xubuntu and still no luck. I'd like  to be sure that 


I've tried everything software-related before I  conclude that the camera is just plain busted.  

  

I tested it with Skype and Cheese. Skype recogonizes the presence of a USB 2.0 camera but the picture is black. 

  

It shows up using the lsusb command: it's a Genesys Logic 1.3 megapixel, usb id 05e3.0505. 

  

It's on the list of webcams supported by UVC.  I tried the solution suggested here [https://answers.launchpad.net/ubuntu/+question/19770](https://answers.launchpad.net/ubuntu/+question/19770) but found that many of the commands didn't work and didn't know what I was doing:

  

"sudo aptitude install subversion" i used the "apt-get" command instead of "aptitude" which did not work

  

"svn co svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc" -->command not found

  

i am also working on installing "eee control" for ubuntu which was recommended in the ubuntu forums using this method: [http://www.matthartley.com/eee-control-ubuntu/](http://www.matthartley.com/eee-control-ubuntu/)  however, "sudo apt-get install eee-control" does not work, the package couldn't be located.  :-/

---

### Post by bkline on 2013-08-27
There's an eee-control package which might be useful in getting the hardware to cooperate:

[http://www.matthartley.com/eee-control-ubuntu/](http://www.matthartley.com/eee-control-ubuntu/)

---

### Post by wildmanne39 on 2013-08-27
*Thread moved to **General Help**.*

---

### Post by casey4 on 2013-09-01
SOLVED 

$ sudo modprobe uvcvideo  to load the kernal  had to add "uvcvideo" to the directory /etc/modules to get it to load automatically.

---

