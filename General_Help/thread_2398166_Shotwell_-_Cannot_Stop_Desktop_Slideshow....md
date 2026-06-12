---
title: "Shotwell - Cannot Stop Desktop Slideshow..."
date: 2018-08-08
forum: General Help
---

### Post by 2CV67 on 2018-08-08
Hi!
I don't normally use Shotwell at all.
But in playing with wallpaper changers, I tried Shotwell's "Desktop Slideshow" using some of my own images.
It was easy to set up & worked OK.

But when I wanted to try different intervals & different transitions, I found I could not get access to any controls!
Hopefully I am just missing something obvious, but I found other people saying the same thing & nobody answering...

So I thought I would just switch it off, but I couldn't find how to do that either!

Finally, I decided to uninstall Shotwell, so used SynApt to "Remove" it.
But the slideshow continued!

I tried using SynApt to reinstall then "Completely Remove" Shotwell.
But the slideshow continues!!

I notice I still have a folder /.local/share/shotwell/wallpaper which contains my images & a "wallpaper.xml" file.
I am tempted to simply remove this folder.

Thanks for any advice on:
-How to modify a Shotwell Desktop Slideshow once it exists
-How to stop/cancel a Shotwell Desktop Slideshow
-Why is my slideshow still working without Shotwell installed?
-What I should do to stop my slideshow & leave things "clean"

Thanks!

---

### Post by 2CV67 on 2018-08-11
I found I could stop the slideshow by going:
Settings > Background > Pictures > Select a picture.

But I would still like some more answers!

---

### Post by tea for one on 2018-08-23
You could also stop the slideshow using the escape key.

However, there is a bug [https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1772878](https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1772878) in Shotwell version 0.28.2, which is the version used in Ubuntu Bionic 18.04. The bug prevented access to the slideshow settings and possibly displayed itself in the problem you mentioned.

This has now been fixed in Shotwell 0.29.91 and you can install this new version by adding the Cosmic repository **deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main** to your sources list.

Hopefully, the later version will solve your problem.

Kind regards

---

