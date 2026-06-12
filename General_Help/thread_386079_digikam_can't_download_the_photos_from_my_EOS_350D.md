---
title: "digikam can't download the photos from my EOS 350D"
date: 2007-03-16
forum: General Help
---

### Post by lowracer on 2007-03-16
I used to be able to download photos from my EOS 350D (Canon Digital Rebel XT), but suddenly today when I tried it, it doesn't work.  When I plug in the camera via USB it is recognized by the OS and digikam will come up but when I tell it to connect to the camera it gives me an error (Failed to connect to camera. Please make sure its connected properly and turned on. Would you like to try again?)  and provides two buttons to take action: Abort or Retry.  Neither has the desired effect.  My images are still in the camera and not on my hard drive.

FWIW, Edgy 6.10, updated religiously, and Digikam 0.8.2 using KDE 3.5.5

Any ideas on how to debug this?

Thanks...

---

### Post by eholcroft on 2007-03-18
This fix worked for me:

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/90978](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/90978)

---

### Post by lowracer on 2007-03-23
I'm not seeing a fix on that page.  What am I missing?
Also, my printers and other USB devices are working fine.  And I've tried the camera on a Mac and it can download fine, so it's not the camera.

---

### Post by jonas.p on 2007-03-30
Hi

I had the same Problem.

Here is the Solution:
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

Jonas

---

### Post by ingo on 2007-04-10
Did the trick for me!

But why has it not been updated yet for 6.10?

---

### Post by ingo on 2007-04-25
I just upgraded to 7.04 and the same problem persists! Again I had to edit the rules file to get my camera working - very strange indeed...

---

### Post by lowracer on 2007-04-29
Upgrading to Feisty 7.04 fixed the problem...

---

