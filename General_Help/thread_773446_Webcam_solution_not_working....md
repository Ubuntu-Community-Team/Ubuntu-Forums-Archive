---
title: "Webcam solution not working..."
date: 2008-04-28
forum: General Help
---

### Post by xxchixorxx on 2008-04-28
Sorry for the cross-post, but I wasn't sure which category to put this question in. 

Re thread: [http://ubuntuforums.org/showthread.php?t=730132](http://ubuntuforums.org/showthread.php?t=730132)


When I type the following as was given in the solution:

udevinfo -a -p $(udevinfo -q path -p /class/video4linux/video2)  

I get the following:
no record for '/class/video4linux/video2' in database

Is there anything else that I'm missing? As in someone else's case, the Logitech STX worked fine upon installation, but when rebooting, it suddenly wasn't being picked up as /dev/video0.  Any help in solving this would be appreciated!

---

