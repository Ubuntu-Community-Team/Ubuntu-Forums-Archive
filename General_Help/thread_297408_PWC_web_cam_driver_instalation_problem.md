---
title: "PWC web cam driver instalation problem"
date: 2006-11-11
forum: General Help
---

### Post by gres on 2006-11-11
I need to install Logitech 4000 pro web cam the driver for the camera is located here: [http://www.saillard.org/linux/pwc/files/](http://www.saillard.org/linux/pwc/files/). Before upgrade from 6.06 to 6.10 it worked good but now it doesn't work. So I desided to compile it from the source. I installed: sudo apt-get install build-essential and followed the instraction here:[http://www.saillard.org/linux/pwc/INSTALL.en](http://www.saillard.org/linux/pwc/INSTALL.en)
but at the stage  
# cd pwc-10.0.12-rc1
# make
it pops up the message :make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.
I made the directory /build in the  /lib/modules/2.6.17-10-386/ and run the program again then it says that there aren't rules to compile the source.
What can I do wiht that problem?

---

### Post by OffHand on 2006-11-11
Use my howto: [http://www.ubuntuforums.org/showthread.php?t=282748](http://www.ubuntuforums.org/showthread.php?t=282748)

Step 3 and 4.

---

### Post by gres on 2006-11-11
Thank you very much! Everytning is working!!!:)

---

### Post by OffHand on 2006-11-11
> **gres said:**
> Thank you very much! Everytning is working!!!:)

No problem  ;)

---

