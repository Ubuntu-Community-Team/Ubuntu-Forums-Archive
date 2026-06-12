---
title: "Internet connection"
date: 2005-08-17
forum: General Help
---

### Post by starvis on 2005-08-17
Hi everybody! Can someone tell me how to set up a dail up connection using ES2838/2839 inernal modem. Thank you. :smile:

---

### Post by joshpelkey on 2005-08-18
Hi **starvis**.  I must warn you that sometimes getting a dial-up modem up and running is a difficult task.  However, it is definitely possible.  First thing to do:  You must download [this](http://linmodems.technion.ac.il/packages/scanModem.gz) program and install it.  Issue these commands to get it to run:

gunzip scanModem.gz
chmod +x scanModem
./scanModem

Now, follow the instructions which appear in the screen. Just hit Enter if you do not understand.  A new subdirectory named Modem was created with several files in it. cd Modem to get into it.  There are a bunch of text files for your viewing pleasure that will hold all the answers as to whether or not  you can get your modem to work and how to get it to work.  Post your ModemData.txt if you want more help from people on this forum, or read the files yourself and try to figure it out!  Good luck.

---

