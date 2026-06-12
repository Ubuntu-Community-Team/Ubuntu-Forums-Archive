---
title: "trust WB-3600r web cam install"
date: 2007-12-29
forum: General Help
---

### Post by garymc1 on 2007-12-29
i am using feisty 7.04
i am trying to install my Trust wb 3600r web cam 

when i run lsusb i get 
Bus 004 Device 003: ID 145f:013d  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

when i unplug the webcam run lsusb i get 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

i have installed camorama but when i run it i get,,, could not connect to video device (/dev/video0).
please check connection.

any ideas ??
Thanks Gary

---

### Post by ilowman on 2008-02-22
Did you ever get this resolved? I have the same problem with that webcam but I'm using Gutsy. I've tried Easycam and Easycam2 but neither work.

lsusb
Bus 008 Device 005: ID 145f:013d
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-02-22
Try using Ekiga to see if cam works/detected there. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by ilowman on 2008-02-23
Thanks for the advice, I just gave ekiga a go but it says no video device detected when setting up. I can't get this to work on my laptop running Hardy either.

---

### Post by linuxwizard on 2008-02-23
ilowman
I just thought maybe Ekiga might work. Not sure what else to tell you. I searched ever where I could think of and can"t find anything on your webcam, which driver you could even try. Found a few Trust webcams here but not yours > [http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html)

---

