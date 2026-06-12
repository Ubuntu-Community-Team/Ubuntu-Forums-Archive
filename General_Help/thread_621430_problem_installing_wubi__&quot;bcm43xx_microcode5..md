---
title: "problem installing wubi : &quot;bcm43xx_microcode5.fw&quot; not available or load failed"
date: 2007-11-23
forum: General Help
---

### Post by cro-marmot on 2007-11-23
Hi !! 
I have tried to install Wubi (on Vista) but i got this error message : 
"[105.248000] bcm43xx : Error : Microcode "bcm43xx_microcode5.fw" not available or load failed" 

What does that mean  ? What can i do to fix it ? 

Thank you in advance.

---

### Post by ago on 2007-11-24
[http://www.linuxquestions.org/questions/linux-hardware-18/bcm43xx-microcode-bcm43xxmicrocode5.fw-not-available-or-load-failed-467164/](http://www.linuxquestions.org/questions/linux-hardware-18/bcm43xx-microcode-bcm43xxmicrocode5.fw-not-available-or-load-failed-467164/)

---

### Post by cro-marmot on 2007-11-28
hello !

I read the page you mentionned but i don't understand what i have to do  :

> You need to get bcm43xx-fwcutter and cut the firmware (from the Windows driver) for the device; [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) 


Do i have to install the driver ? from Windows ?  How can i do this ? 

Thank you.

---

### Post by ago on 2007-11-28
More likely extract the firmware from within the windows driver and then use ndiswrapper with it.

---

### Post by abn91c on 2007-11-28
this is what i did with my dell laptop and kubuntu:  after you get to the desktop make sure your broadcomm card is inserted, if using a laptop go here [http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)

download the driver listed in the link, you may need to copy file to a Jump drive. then go to the file, right click and install using gdebi if you have 7.10 ubuntu/kubuntu or actions>install kubuntu package if tha is the verssion you are using. Thsi is the only driver file that works for me "out of the box". It works for any debian based linux distro broadcomm 43xx wireless card. I tried on a Linksys and belkin card

---

