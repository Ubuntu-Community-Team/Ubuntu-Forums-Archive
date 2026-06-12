---
title: "USB Camera suddenly can't be found any longer."
date: 2013-01-31
forum: General Help
---

### Post by jiapei100 on 2013-01-31
Hi, all:

My environment: Ubuntu 12.04
Logitech Pro 9000 USB webcam

I'm debugging one of my programs which relies on the USB webcam. However, sometimes, I need to stop running my program in the middle. And, I would like to re-debug my program once again after stopping it. The webcam suddenly can't be found any longer. By running **lsusb**, this USB webcam cannot be found any longer.


I'm just wondering is there any command line for me to restart something in **/dev/xxx** ? so that I can re-use my webcam without rebooting Ubuntu ?


Thank you so much...

Best Regards
Pei

---

### Post by no2498 on 2013-02-02
are you turning your debugging program off all the way
or are you just pausing it
if your just pausing it. its showing the cam as still on
thats why lsusb cant find it

john

---

### Post by jiapei100 on 2013-02-02
Hi, thank you John. Thanks for your reply.

In fact, I stopped debugging the program, but I did see the camera is still on. ^_^  Till now, I've got no idea why the Logitech 9000 Pro always kept on even after I stopped my program. I'm 100% sure it's not pause but stop.

Then, is there a method that I can avoid this? Say, whenever the program is stopped (no matter what reason it is), the camera will be able to automatically turned off?


Cheers
Pei



> **no2498 said:**
> are you turning your debugging program off all the way
or are you just pausing it
if your just pausing it. its showing the cam as still on
thats why lsusb cant find it

john

---

