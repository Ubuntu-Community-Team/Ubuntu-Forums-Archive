---
title: "iPod / Digital Camera"
date: 2006-12-24
forum: General Help
---

### Post by LanceM on 2006-12-24
I used [[COLOR="Blue"]this[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=321397&highlight=ipod") thread to get my ipod to work with Ubuntu. Now when I plug in my camera i get this error:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Any ideas?

[B]
##EDIT##[/B]
Found the answer [[COLOR="Blue"]here[/COLOR]]("https://launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/64146/comments/10")

---

### Post by fragos on 2006-12-24
For what ever reason your camera is being assigned to a /dev/video{n} that is already in use.  I recognize one of the drivers mentioned as a webcam driver.  Normaly video devices are mounted with sequencial numbers video0, video1 and etc.  Applications will need to be configured for the corect /dev/video{n}.  The Howto you followed has a lot of command line which although may work was probably not necessary since Ubuntu seems to support ipods directly.  Perhaps your Howto was a mixed blessing.  I'm running Ubuntu 6.10 and have noticed a problem with more than one video device.  I've a TV card and a webcam and /dev/video0 and 1 mounts are sometimes swapped.  A bit of a pain because I have to edit application configurations when they're swapped.  This may not be part of your current problem but with mulitple video devices it may impact you in the future.

---

