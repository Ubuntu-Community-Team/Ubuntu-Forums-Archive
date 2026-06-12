---
title: "Problem with Ubuntu 11.10 - no Xwindows, and USB flash drives aren't seen"
date: 2013-03-26
forum: General Help
---

### Post by mathprof on 2013-03-26
HELP!

I was trying to follow the directions here
[http://www.r-tutor.com/gpu-computing...cuda5.0-ubuntu]("http://www.r-tutor.com/gpu-computing/cuda-installation/cuda5.0-ubuntu") 
and got into trouble.

I didn't get far, just to the sentence:
"Now you can reboot the system at this point for the change to take effect."

Rebooting, I no longer could boot up Xwindows, though I still can access  a terminal.   But I don't know how to undo whatever damage I caused.

I even tried to boot off of a flash drive (so I could reinstall Ubuntu), but my system no longer seems to recognize USB drives.

Any ideas what I can do to undo the damage I've wrought?  

Thanks!

---

### Post by ManamiVixen on 2013-03-26
That article looks like it was written by a monkey! 

> # /etc/modprobe.d/blacklist-nouveau.conf 
blacklist nvidiafb 
blacklist nouveau 
blacklist rivafb 
blacklist rivatv 
blacklist vga16fb 
options nouveau modeset=0        

That basically disables ALL the Nvidia drivers! How does he expect you to use an X Session with no Nvidia video drivers loaded!

BUT he may also assume you installed the proprietary driver before hand. Have you?

---

### Post by mathprof on 2013-03-26
No, that stuff was to be installed AFTER.  Is there a way to undo all that blacklisting??

---

