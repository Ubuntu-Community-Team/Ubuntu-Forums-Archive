---
title: "Camera Installation CD Won't Install?"
date: 2012-11-04
forum: General Help
---

### Post by Lizabelle on 2012-11-04
I have a 12.04 Ubuntu OS, and I've been trying to install my FujiFilm FinePix camera. I put the CD into the drive, and it shows up as a collection of files. 
I am not very much of a techie- could someone please tell me how to get it to run/install the software?

---

### Post by Tank Jr on 2012-11-04
Does the CD have the software for Linux? You may want to check the box.
For my Canon camera I didn't need to install anything--shotwell worked out of the box for me. It can import pictures and save them in a folder according to date, and also publish to Facebook.

---

### Post by ajgreeny on 2012-11-04
That CD will be just for Windows and possibly Mac.

Just plug in your camera and see if it is detected by the system;  my Fuji Finepix Bridge camera (can't now remember the model number) worked without a problem, though in fact I always used a card reader as it was so much speedier than plugging in the camera itself.

It was possible, however, to use that camera as a webcam with no difficulty, and just like Tank Jr, I didn't have to install anything to get it to work.

The various programs they give you on the CD to edit, manage and view photos are  usually not worth installing, in any case; much better to use something  you already have and know.  For that I mostly use digikam, in spite of  using the gnome desktop, as I think it is much better than shotwell or  f-spot, but I also like gthumb as a photo management application as  well.

---

### Post by Lizabelle on 2012-11-14
Okay, I tried just plugging the camera in- nothing. My laptop didn't even recognize it. I'm very reluctant to install the software on someone else's computer, since I don't like to share my photos. 
I already have editing software that I love. I just need a way for my computer to say "Here's your pictures!"

---

### Post by philinux on 2012-11-14
> **Lizabelle said:**
> Okay, I tried just plugging the camera in- nothing. My laptop didn't even recognize it. I'm very reluctant to install the software on someone else's computer, since I don't like to share my photos. 
I already have editing software that I love. I just need a way for my computer to say "Here's your pictures!"

With the camera plugged in to usb port open a terminal using ctrl+alt+t

Then type in lsusb and hit return. Thats a lower case L. Copy and paste back here what it shows.

Also which model is the cam.

---

### Post by Cheesemill on 2012-11-14
You may just need to install [gphoto2]("apt://gphoto2") to add support for your camera to the system.
Cameras supported by gphoto2 are listed [here]("http://www.gphoto.org/proj/libgphoto2/support.php").

---

### Post by eric-yorba on 2012-11-14
You might consider popping the memory card out of your camera and plugging it into your computer directly, or into a USB card reader if your computer doesn't have an internal one.

---

### Post by Lizabelle on 2012-11-14
> **philinux said:**
> With the camera plugged in to usb port open a terminal using ctrl+alt+t

Then type in lsusb and hit return. Thats a lower case L. Copy and paste back here what it shows.

Also which model is the cam.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 005 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

The camera's model is 
FINEPIX T400-T410
FINEPIX T350-T360
(That's what it says on the manual.)

And Cheesemill: I installed the gphoto2, and it didn't help. Probably because my camera wasn't on the list that was attached. ;) Thanks for the help, though!

---

### Post by timgood on 2012-11-15
You have remembered to turn the camera on while it is connected? Just checking...:)

---

### Post by 3rdalbum on 2012-11-15
We have some Fuji cameras at work. You must turn it on while it is connected to USB.

The Windows software is not only unnecessary, but it wouldn't work on Linux anyway.

---

