---
title: "usb device like a tv-box with em2820,saa7113h?"
date: 2007-05-08
forum: General Help
---

### Post by Newlad on 2007-05-08
i have a convert card,which convert analog signal to usb stream like the utv310( a tv-box),
the lsusb give the output:
Bus 003 Device 002: ID eb1a:2821 eMPIA Technology, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

i modprope the em28xx module ,but it not create the node /dev/video0

and when i use xawtv to open it 

sudo xawtv ;

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  67
  Current serial number in output stream:  67

and i use sudo xawtv -nodga

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available


i have google the "eb1a:2821" ,and i found a thread:
[http://ubuntuforums.org/showthread.php?t=158225](http://ubuntuforums.org/showthread.php?t=158225) ,butthe [http://linuxtv.org/hg/~mrechberger/v4l-dvb](http://linuxtv.org/hg/~mrechberger/v4l-dvb) have nothing to download


thanks

---

### Post by Newlad on 2007-05-14
ry to download and compile from
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)

This one compiled with kernel 2.6.20.
[http://mcentral.de/wiki/index.php/Em2880/Status](http://mcentral.de/wiki/index.php/Em2880/Status)

---

