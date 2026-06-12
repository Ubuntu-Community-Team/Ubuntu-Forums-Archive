---
title: "which nVidia drivers should I choose?"
date: 2013-02-22
forum: General Help
---

### Post by lamb123 on 2013-02-22
for gtx 660

[[IMG]http://i.imgur.com/5ryAvkp.png[/IMG]]("http://i.imgur.com/5ryAvkp.png")

Currently using X.Org by default.

So when I tried the first and third one, after rebooting my main monitor did not start and my left monitor had no launcher. Also window title/borders were gone.

Got my confirmation that linux is still as laughable as ever and will uninstall this crap.

---

### Post by duke.tim on 2013-02-23
For ease and stability use Xorg nouveau. 
It was designed by the Open Source community and has the advantage of being stable.
It takes time to reverse engineer drivers for full support.

If you are willing to put up with a bit of work some other people might be able to help you install the proprietary NVidia drivers. If you are willing to try here is a starter assuming you use the geforce series [http://www.geforce.com/drivers](http://www.geforce.com/drivers)
[http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/index.html]("http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/index.html")

The issues with the Drivers is on nvidia's side, as Linus Torvalds said "Nvidia has been the single worst company we have ever worked with" --http://www.geek.com/articles/games/torvalds-rant-against-nvidia-works-new-linux-drivers-double-gaming-performance-2012117/

---

### Post by lamb123 on 2013-02-23
noveau is unusable, super slow - everything lags

---

### Post by Juniorr on 2013-02-23
On 12.04 I use 310 Experimental, because I play with Steam.
On 12.10 I'm experiencing errors, so I'd suggest you wait for a response there =P

[http://ubuntuforums.org/showthread.php?t=2119216](http://ubuntuforums.org/showthread.php?t=2119216)

---

### Post by lamb123 on 2013-02-23
will try 12.04 then

---

### Post by BriGaid on 2013-02-23
I'm running 12.04 with a GTX 650 Ti 2GB SSC card. I had a lot of issues with compiz running any of the drivers through the x-swat or just straight repositories through joystick. I removed everything graphics-related and installed the latest drivers from Nividia directly. It is running stellar now in all of my games in Steam as well as those outside.

[http://www.nvidia.com/object/linux-display-amd64-310.32-driver.html]("http://www.nvidia.com/object/linux-display-amd64-310.32-driver.html")

---

### Post by Frogs Hair on 2013-02-23
I use the experimental 304 on 12.10 with an 8 series card (:ojoy!) . The Nvidia current didn't work well for me on 12.10.(:()

---

### Post by oldfred on 2013-02-23
With my old nVidia 9600GT I had issues with 12.10. I had to install headers first. Only then the install of the nVidia drivers would work.

       # You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

    
With my older card I did use nvidia-current-update, but those with newer cards may need the experimental.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

