---
title: "iMon Remote with kernel-lirc"
date: 2012-11-27
forum: General Help
---

### Post by Acer8888 on 2012-11-27
Hello I have been looking and looking for how to setup my iMon Pad remote with my Myth frontend. I currently have mythbuntu 12.04 installed and have read the kernel supports remote control command straight out of the box (which it does, to a point). From what i have read online (and i could be wrong) installing lirc is not needed anylonger and that it seems to be old out of date software. What i am running into is that only certain general commands work such as up,down,left,right,enter,exit. Numbers, pause,play etc are not working inside of myth. I have install ir-keytable, and issued a ir-keytable -t command and it reports every button i press on the remote. I have tried editing myth keys and pressing the remote button, but nothing shows up.

here is the result of ir-keytable if it helps

Found /sys/class/rc/rc0/ (/dev/input/event4) with:
    Driver imon, table rc-imon-pad
    Supported protocols: RC-6 other 
    Enabled protocols: 
    Repeat delay = 500 ms, repeat period = 125 ms

What am i missing? I havnt been using ubuntu for a long time and i am slowly learning the ways. 

Thank you in advanced for you help!!

---

