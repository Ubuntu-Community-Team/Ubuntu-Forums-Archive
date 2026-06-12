---
title: "oh no.."
date: 2007-09-19
forum: General Help
---

### Post by nerojrnde on 2007-09-19
i just installed a nvidia package fro apt-get. ran all of that, went to config and enable. it said the file had to be restarted, so i did. turns out it wont run graphic. is there anyway to load my old xorg file? 

ahh i miss ubuntu..i hate this windows desktop!!

thanks for any help you can provide getting me back on!

---

### Post by nerojrnde on 2007-09-19
ok i just rebooted and im at a screen that reads:

Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?


Yes or No.

Hmm?

unless there is a guide for this i cant find

---

### Post by nerojrnde on 2007-09-19
please..i dont wanna wipe my hd..damn

---

### Post by PurposeOfReason on 2007-09-19
Did you make a backup? If not, boot into recovery mode and type the following

sudo dpkg-reconfigure xserver-xorg

---

