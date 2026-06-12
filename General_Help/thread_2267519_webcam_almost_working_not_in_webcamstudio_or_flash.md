---
title: "webcam almost working not in webcamstudio or flash"
date: 2015-03-02
forum: General Help
---

### Post by linda4 on 2015-03-02
hi. im having trouble getting flash and webcamstudio to recognize my external webcam. 

if i use command line vlc to view /dev/video2 it does get video from the external cam. 
the cam shows up in lsusb.
i tried using webcam studio (hoping as a possible solution i could use this to get a virtual cam flash would recognize ).
webcamstudio detects two cams (my integrated and my external) but if i try to capture from the external its just showing a black screen.
gstreamer shows both cams. i can select the external as default but flash still doesnt see it.
im kind of stuck. please assist / advise. thanks. 


ubuntu@ubuntu:~$ lsusb
Bus 002 Device 002: ID 0781:5581 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by linda4 on 2015-03-02
ok update 

i tried running chrome with a preload 

" #!/bin/bash LD_PRELOAD="/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so" /usr/bin/google-chrome
"

which allows the quickcam to show up in the available cams list in chrome / flash.  
that's good.

unfortunately when i run it that way even though both cams show up in the list neither work.

i'm thinking maybe i need to run chrome as root to get permission to access cams?  so i tried that . chrome is being difficult about being ran as root. i create --user-data-dir and passed that in then
i get  IBUS errors (IBUS file not owned by root) and chrome wont even load.

still stuck. doh!

---

### Post by linda4 on 2015-03-10
well just in case anyone finds this and is having the same problem i will let u know how i fixed it. 
i never could get the quickcam express going with chrome or anything else. 
just one problem after another. not saying u cant make it work at all just i didnt have any success that way. 

what i did was go and buy a logitech  c270. also went to the chrome site and got the latest linux version.
it was all recognized right away and no trouble. i can use flash to select the cam and allow buttons in chrome and the
c270 is available and just works.

---

