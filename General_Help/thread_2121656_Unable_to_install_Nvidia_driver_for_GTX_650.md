---
title: "Unable to install Nvidia driver for GTX 650?"
date: 2013-03-02
forum: General Help
---

### Post by rosefox911 on 2013-03-02
Hey guys,

I just got a new nvidia gtx 650 for my uuntu home server. I plan to run dolphin emulator off it. However, after installing the drivers  I just see a black screen after I get past GRUB. I have tried installing it both through Additional drivers and using sudo apt-get install nvidia-current. Both produce the same result. The only way to get it to not be a black screen is to remove all drivers using apt-get remove nvidia-current. Any suggestions? Thank you!

Jorge

---

### Post by The Cog on 2013-03-02
Try the very latest drivers in synaptic - I think they're called experimental-310 or something like that. I gather they fix several problems.

---

### Post by rosefox911 on 2013-03-02
> **The Cog said:**
> Try the very latest drivers in synaptic - I think they're called experimental-310 or something like that. I gather they fix several problems.
Hey,

I gave that a shot. Unfortunately, its still a black screen past GRUB (blinking underscore and then completely black). Any other suggestions?

---

### Post by oldfred on 2013-03-02
Did you install 12.10 or 12.04.2?

 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 

then install the new nVidia driver.

---

### Post by rosefox911 on 2013-03-02
> **oldfred said:**
> Did you install 12.10 or 12.04.2?

 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 

then install the new nVidia driver.
Hey!
[FONT=arial]
I have 12.10 installed. I've tried updating the header files for the  kernel using apt-get. I ran everything on that link as well, still having the same issue with [COLOR=#000000]*sudo apt-get install nvidia-experimental-304. Let me know if anything else comes to mind. Thank you!*[/COLOR][/FONT]

---

