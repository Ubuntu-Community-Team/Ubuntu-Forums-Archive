---
title: "Ubuntu freezes for unknown reason"
date: 2013-11-13
forum: General Help
---

### Post by adinatbust on 2013-11-13
Hello,

i have got the following problem with my ubuntu 13.10 (amd64) installation. While I am working, ubuntu slowly freezes in several phases until it's completely frozen. When music is running, i can specifiy more phases of freezing like
1) the GUI does not responds any more, but mouse cursor is still moving, and music is still running
2) also the cursor freezes, music still running, some keyboard commands working but screen is frozen
3) complete freeze, nothing works.

during the installation i tried to install 12.04 LTS with no success, with these symptoms but direct after boot. 

First I thought, the RAM is broken, so did 3 hours of memtest with livelinux. no errors were found. After changing the hard disk, i had managed to install 13.04 (later update on 13.10) so the system had worked quite well.

Now these freezes appear absolutelly spontanios while working. The only thing I prupose is, that a freeze comes often when more applications are running when less. But this is no fact. 

All the hardware ist new, but the hard disk is not. 

This is my hardware: 
CPU: AMD Phenom(tm) II X4 B55 Processor × 4 
Hostbridge: AMD/ATI RX780/RX790
Graphic: NVIDIA GeForce GT 630 (for running 2 monitors)
Memory: 8GB

How can I find what does causing these crashes/freezes? Is it a problem with the hardware or with ubuntu its self?

Thank you for advice

David

---

### Post by adinatbust on 2013-11-13
Update: it seems to be the card. I am now running the nvidia binary driver. Using them i got the crashes. Using the nvidia-current driver makes my system completely unusable...after installing them i had to run ubuntu in recovery mode to kill the drivers to make my system running again.....what should I do?

---

