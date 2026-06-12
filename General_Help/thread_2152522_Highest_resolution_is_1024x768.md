---
title: "Highest resolution is 1024x768"
date: 2013-06-08
forum: General Help
---

### Post by tarshoduze on 2013-06-08
Hi,
I am using Xubuntu 12.10, and just like Ubuntu 12.04.1, it can't use 1280x1024 which is my monitor's resolution. How do I fix it?
I have Intel 82865g integrated graphics.
I'd happily supply more needed details.
Thanks!

---

### Post by CatKiller on 2013-06-08
It's because your monitor isn't passing the EDID information that would let it be automatically detected. I believe you need to add the resolution with XRandR.

---

### Post by sum1nil on 2013-06-08
Here is the link to the Ubuntu Wiki on how to use Xrandr to test resolutions on the fly even:  
  [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

You may want to check lsmod to see if an actual 'intel' module is being loaded instead of something like 'intelfb'. If it is not, then you can download 
Intel modules by 'sudo apt-get install xserver-xorg-video-intel'. There is also a detailed adventure about replacing Intel video modules here 
but it is a little dated in places: 
  [http://ubuntuforums.org/showthread.php?t=1879121](http://ubuntuforums.org/showthread.php?t=1879121)

---

