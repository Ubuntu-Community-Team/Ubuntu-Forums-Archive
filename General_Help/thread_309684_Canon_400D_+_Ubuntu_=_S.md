---
title: "Canon 400D + Ubuntu = :S"
date: 2006-11-30
forum: General Help
---

### Post by cenithx on 2006-11-30
When I try to import photos from my Canon 400D I get the following error:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Can anyone help?

I have digiKam installed as well, but it doesn't have support for the 400D.

](*,)

---

### Post by cenithx on 2006-11-30
Got it working.

For 400D owners, you'll probably have to do this:

Edit:
**sudo gedit /etc/udev/rules.d/45-libgphoto2.rules**

Add to the bottom of the list: 
**SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3110", MODE="0660", GROUP="plugdev"**

Save and close.

Restart udev:
**sudo /etc/init.d/udev restart**

---

### Post by rutty on 2006-12-18
I needed this!

Thanks a bunch - I was about to get a bit frustrated with my lovely new camera :cool:

---

### Post by &amp;wi*m#~10+q on 2007-06-14
This is not working for me. :(

---

