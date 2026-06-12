---
title: "Slow boot/question"
date: 2016-09-18
forum: General Help
---

### Post by 5hutd0wn on 2016-09-18
Hi im a noob to ubuntu and am already having problems:

First im using a samsung t3 SSD and my boot time is over 1:30 min.   On a very crappy usb key i get a 10sec boot so i think somethings wrong. 
My main pc is a DELL latitude E5450 and the year i got has a faulty accelerometer Dell issued a patch that disables it but could it still slow down boot?   I ran a command and found that their was a 60-90sec delay between processes.  Could this be a timeout trying to load drivers for this device?
If so how would i dissable it fully.  

Also i installed the elementary os de and it screwed up ubuntu with the top bars and terminal.  I uninstalled it and removed ppa's but at boot when i push f12 and select ubuntu after that it says: elamentary, elementary settings, install elementary
Is this a problem?  I dont see any problems but is elementary running in the background?  

Finaly i saw a thing online about dont format ssd's because it gets filled with zeros.  when i installed i formatted it with gparted but it hadent had anything on it previously.   My ssd is super fast and doesnt lag or anything but i dont want to waste write cycles or anything.


ps: sry for my spelling (i blame public highschool lol)  and the post that is probaly to long or irreverent or something that will probably get removed.

One more thing in software and updates the first tab says debian software instead of ubuntu software.  is this because of the elementary thing? and how do i fix this?

---

### Post by oldfred on 2016-09-18
Did you attempt to share /boot or /home with Elementary? 
That will lead to issues like you are having.

Formatting will not clear or fill any drive with zeros. But most of the secure erase applications do write all zeros. But trim clears unused blocks anyway.

Post top few lines from this:
 systemd-analyze blame

---

### Post by 5hutd0wn on 2016-09-18
Thankyou No i only installed the desktop enviroment pantheon but it seems i corrupted some important files Im reinstalling right now.

---

