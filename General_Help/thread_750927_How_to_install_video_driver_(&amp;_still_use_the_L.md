---
title: "How to install video driver (&amp; still use the Live CD?)"
date: 2008-04-10
forum: General Help
---

### Post by stanstr on 2008-04-10
I'd like to get an old PC running Ubuntu 7.10, and so far have only run the Live CD . It seems to work, and I'm sure it'll run better once I install it. 

The PC is an old AMD K6 350MHz with only 256M RAM and currently  has W '98 installed and runs somewhat ok. There is nothing important on it and I'd like to 'Ubuntu it'.

Runnning the Live CD I can only get 800 x 600 (or 640 x 400) screen resolution. The monitor can show 1280 x 1024. The video card is a 3D Blaster Banshee PCI/AGP by Creative Technology. 

Assuming I just need new video driver(s), what does it take? Where do I look? How do I install it?

And the dumb question: Is there some way I can get the driver and and 'install' it while using the Live CD?

---

### Post by Rocket2DMn on 2008-04-10
The LiveCD doesn't have very good video driver support, so you should go ahead and try installing to see what happens.  It might find one of the less well-known drivers that will work with your card (since open source or proprietary ati and nvidia drivers won't work).  In the very least, you will be able to use the "vesa" fallback driver which has limited capabilities but tends to work on everything, minus fancy graphics like Compiz Fusion.
To my knowledge, there are no restricted drivers for cards other than ati's and nvidia's, so if it doesn't work out of the box, the chances are you'll just have to use the "vesa" driver.

You can install drivers from the LiveCD, but they disappear when you reboot.  But again, I don't know of any specific drivers for that card, I just know that sometimes people with some of the stranger cards out there are able to use specific drivers that are detected during the install process.

---

