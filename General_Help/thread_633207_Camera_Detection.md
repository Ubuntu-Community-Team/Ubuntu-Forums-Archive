---
title: "Camera Detection"
date: 2007-12-06
forum: General Help
---

### Post by Damanther on 2007-12-06
OK, I don't believe this problem is specifically related to the other usb problems that have been posted, but I could be wrong. Here is my issue:

I did the upgrade to gutsy, everything is going well with the usb stuff. My usb stick gets recognized and automounted, my usb external hard drive the same thing. The problem is now my camera. It is a Panasonic DMC-FX01 if that matters. It has 2 usb modes, standard usb mode, and a PTP mode. Under feisty I always used the standard usb mode and I could download the pictures via digikam, or by just using a file manger and copying the files from the mounted camera drive.

In gutsy, the normal usb does not work. It recognizes the device as a mass storage camera and puts an icon on my desktop, but I cannot mount it or browse to it with dolphin, and digikam certainly cannot connect to it.

If I use the PTP mode, digikam can now see the camera, and I can download the still image jpegs, and I can browse to it with dolphin.( dolphin says it is using a gphotosomething driver to display the contents of the device ). That would be fine, with the exception that the camera also records small movie files in quicktime format. Neither digikam or dolphin can see these files.

After all that, how can I get the camera to look like a standard usb stick like it used to under feisty??
I've been using my one windows laptop which still loads it as a standard usb stick to retrieve the .mov files but that makes me feel icky and I shouldn't have to resort to that.

---

### Post by Damanther on 2007-12-10
Surely someone knows how to make this thing behave like a usb stick. Other usb drives work fine, but the camera no longer does since gutsy.

---

### Post by gelin on 2008-01-08
I've got the same problem.

My camera is Panasonic DMC-LZ5. Sometimes it's detected as "USB Mass Storage Interface" with address system:/media/camera/, and digiKam detects it as Panasonic DMC-FZ20. This isn't work. And sometimes it's detected as common "Storage Media" which should work fine. 

But most often it's detected in both ways! And when I start to download photos (with the second, correct, way), disk disappears. And sometimes my camera hangs up and not responding! I suppose it's caused by a such "double" access.

PictBridge (PTP) mode is detected as "USB Imaging Interface" and works fine.

---

### Post by dmatej on 2008-03-08
I have the same problem with DMC-FZ50. If I want to download videos I have to use MS Windows or another computer with feisty :(
Have you found any solution?

---

### Post by Neobuntu on 2008-03-10
I have the same exact problem with my new Panasonic DMC-FZ-18. Why?

Are the cameras changing or is it Kubuntu 7.10? Do we need a Kernel upgrade? 

It'd be nice if we could keep the gains we make with open software.

---

### Post by jon zendatta on 2008-04-09
yes i have this problem with panasonic dmc-f27. it was detected no problem in fiesty but not on gutsy.
io/ library error!
cheers

---

### Post by The Devil Is A Squirrel on 2008-04-10
I have the same issue with my Panasonic DMC-FZ50 and Kubuntu 7.10.

---

### Post by jon zendatta on 2008-05-08
hell0 people
any joy here yet? wondering if any upgraded to 8.04 and got camera detection
cheers

---

### Post by jozok on 2008-06-28
I have similar problem with DMC-FZ10. I have reported it to KDE bugs report [http://bugs.kde.org/show_bug.cgi?id=127931#c4](http://bugs.kde.org/show_bug.cgi?id=127931#c4)
Konqueror cannot mount usb connected camera as a filesystem. Nautilus in GNOME has no problem.

---

