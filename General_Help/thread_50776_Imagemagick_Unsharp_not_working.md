---
title: "Imagemagick Unsharp not working"
date: 2005-07-21
forum: General Help
---

### Post by SteveF on 2005-07-21
I'm trying to perform batch processing on some images.  All of the parameters I've been passing convert have worked except the unsharp mask.  I can't seem to get it to do anything.  I've removed all parameters and am just playing with unsharp mask.  Every setting I throw at it returns images that look exactly the same as the original.  I have the unsharp working under the Windows version of Imagemagick so I'm pretty sure the parameters I use should show some differences.

The images I'm using are direct from a 5mp camera.  The size of the images is 2592x1944 pixels.

I call:

convert 5x3+1+0 imagename newimagename

I've tried with parameters like (some should be well over sharpened - just trying to get some differences to show):
3x5+1+0
20x10+1+0
20x20+1+0
20x10+2+0
5x3+2+0

Looking for some advice.  Is this an issue with the version packaged with Ubuntu or am I missing something?

Thanks,

Steve

---

