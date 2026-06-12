---
title: "fglrx"
date: 2005-10-29
forum: General Help
---

### Post by jhawsey on 2005-10-29
I am running breezy and have installed fglrx for my ATI 9600 pro to get 3d acceleration.  This worked great.  However, when i switch over to the fglrx driver, I no longer can get my 1680x1050 res.  I have to switch back to the ati driver with no acceleration to get that res.  The weird thing is that this particular resolution shows up when I run "dpkg-reconfigure xserver-xorg"  :confused:

---

### Post by munkymonkjr on 2005-10-30
question. are you using the restricted modules to have fglrx? if so, that version of the driver has screwed up widescreen resolutions. My laptop also gets shitty resolution when i install the restricted modules. So pretty much what you gotta do is install the latest version from ATI's website. 

this should help you install the latest version:
[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)


btw, if your wireless is also in the restricted modules (if you have Atheros for example....like i do) you'll need to install the drivers from scratch (either build the native driver like Madwifi or use ndiswrapper)

---

### Post by jhawsey on 2005-10-30
I am not sure if I am using the restricted modules...how do I check?  I am still pretty much a novice to this.
Thanks for your input.

---

