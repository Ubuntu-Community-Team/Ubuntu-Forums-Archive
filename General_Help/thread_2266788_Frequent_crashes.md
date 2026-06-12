---
title: "Frequent crashes"
date: 2015-02-25
forum: General Help
---

### Post by John_Rose on 2015-02-25
Hello,
 

 I am running 12.04 LTS avec kernel version 3.2.0-76-generic-pae  under Gnome Classic desktop on a Dell Vostro notebook.
 

 Suddenly starting about 3 weeks ago my system crashes (5 times so far). There are messages from Ubuntu on the screen upon crash but too fast to see. The** /var/log/apport.log file does not show any messages upon crash (at least not the last one). The /var/log/messages file is not activated. This started happening just after the Dell technician installed a bluetooth card (previously missing) but perhaps just coincidence.**

 

 **Could someone please walk me through the steps to find out what is happening?**
 

 **	Thanks and best regards,**
 **	John**

---

### Post by Hastur_The_Unspeak on 2015-02-25
Well, lemme just say you're not alone in the "unwanted crashes" department, as I've had such errors as well. If the logs are coming up blank like they were for me, I would recommend talking matters into your own hands. If I were you, I would use an ubuntu live USB or live CD, and use it to run memtest on your rig. The memtest will perform a variety of stress tests and whatnot, and determine errors with your hardware. Then, I would advise looking up said errors after they are spat out, and then going from there

---

