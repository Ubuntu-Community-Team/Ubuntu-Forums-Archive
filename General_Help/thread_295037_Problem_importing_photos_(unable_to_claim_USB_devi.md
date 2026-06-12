---
title: "Problem importing photos (unable to claim USB device)"
date: 2006-11-07
forum: General Help
---

### Post by GeirG on 2006-11-07
Hi,
I just received my Canon G7 camera and looked forward to pluging it into my PC to see how well it was handeled by Edgy. Unfortunately this is taking a bit longer than I hoped for, although I'm sure it won't be long :-D 

When I connect the camera to my PC, a window pops up and asks what I want to do. I click 'Import Photos', and the following message appears:

"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

Now, I guess this means that either some "wrong" driver takes hold of my camera (or rather the USB device), or some perrmission setting is wrong. This is all well and good, except I don't really know what to do, and where to do it.

Any ideas? :-k 

TIA

---

### Post by stream303 on 2006-11-07
The G7 is just a tad too new.  Much like the A630/640.  They're just too new even tough uPTP should've taken care of it. (I encountered the exact error you had with my 630)  Guess we'll have to wait for an update.

In the meantime, I use a card reader, or one of those fancy Sandisk cards that snap in half to a built-in usb.

---

### Post by fragos on 2006-11-07
My Canon Powershot S3 IS is a new model but it works as expected.

---

### Post by GeirG on 2006-11-08
Yeah, I know its new, but if that was the problem I would have expected a "unknown model" type of error. 
This seems a bit more specific, like some unfavorable default configuration, if you catch my drift.

Thanks for the reply though :-)

I guess I better get hold of a card reader for my vacation to be on the safe side...

---

### Post by fragos on 2006-11-08
Card readers are inexpensive and have many other uses.

---

### Post by GeirG on 2006-11-09
Found the solution: 

[https://launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/64146)

:-)

---

