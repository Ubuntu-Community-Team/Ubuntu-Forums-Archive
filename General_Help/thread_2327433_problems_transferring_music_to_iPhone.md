---
title: "problems transferring music to iPhone"
date: 2016-06-10
forum: General Help
---

### Post by lbeidler on 2016-06-10
running 16.04, I have an iphone 5 running iOS 9. I also have a 5S that shows this same behavior. 

here's what I want to do:
I just want to load music onto my iPhone!

what I've done:
- updated libimobiledevice2
- I just installed 16.04 the other night, so Rhythmbox & Clementine are up to date
- i've used ifuse to mount it

Here's what I CAN do: 
[LIST=1]
[*]I can connect my phone to my laptop and it shows up as a digital camera, and I can transfer photos to & from the photos (DCIM) folder
[*]When I run dmesg, it shows that it recognizes my iPhone.
[*]When I run Clementine, the phone shows up in the Devices section of Clementine.
[*]I can mount it using ifuse and see the folder structure
[/LIST]

Here's what I can't do:
Clementine - 
    as soon as I try to send a file to the phone using Clementine, Clementine exits
    Even though I have music loaded on my phone, when I double-click on it in Clementine, it says "zero songs"
Rhytmbox -
    the phone never shows up as a device in Rhythmbox
ifuse - 
     no matter what I do, I can't seem to copy files to the right place so that iMusic sees them & I can play them. 



Perhaps you can guess that I've tried a bunch of things so far, but am still coming up empty. Please help!
Thanks.

---

### Post by X-RED_Tech on 2016-06-10
Is there some toggle between PTP and MTP like in Android? It's a setting in the phone itself.
If you can't change that from the phone itself I doubt there's any "magic" Ubuntu can do about it. But besides the common knowledge that Apple doesn't support Linux at all, I know nothing about iPhones.

---

### Post by kevdog on 2016-06-11
I found this as a reference but have never tried it:[http://www.dedoimedo.com/computers/linux-iphone-6.html](http://www.dedoimedo.com/computers/linux-iphone-6.html)

---

### Post by lbeidler on 2016-06-11
Yup, thats' where I heard about ifuse and mounting the files structure.   can't figure out how to put the music files in the right place...

---

### Post by X-RED_Tech on 2016-06-11
If nothing works use some cloud and save yourself a lot of trouble.

---

