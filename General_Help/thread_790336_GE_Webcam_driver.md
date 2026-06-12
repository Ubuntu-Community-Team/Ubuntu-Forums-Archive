---
title: "GE Webcam driver"
date: 2008-05-11
forum: General Help
---

### Post by raven302 on 2008-05-11
Got everything working sweet on my new Linux install, cept.... my webcam.

It's a GE one my wife has had forever. I'm unsure of the model but GE does not offer an installation for it on Linux. :(

It's a GE 98604 Easycam Pro. "in Windows Anyway..."

Any insight appreciated!

---

### Post by linuxwizard on 2008-05-11
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Work with the Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If the webcam does not work post the results of the command > lsusb

---

### Post by raven302 on 2008-05-11
Did that, I know the RTFM slogan... :P I've looked all over for a solution. I plugged another crappy one in(MicroSolutions) and it works just fine.

---

### Post by raven302 on 2008-05-11
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
Bus 001 Device 004: ID 03f0:1604 Hewlett-Packard DeskJet 940c
Bus 001 Device 001: ID 0000:0000

---

### Post by ghost_ryder35 on 2008-05-11
so this is the GE webcam
Bus 001 Device 005: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
or is that the crappy one micro solutions?

---

