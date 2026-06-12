---
title: "How do I undo a patch?"
date: 2007-03-12
forum: General Help
---

### Post by starchildmom on 2007-03-12
I have been running Edgy since it was released with no problems, at least not unexpected ones :) However, this weekend I got a second generation Ipod Nano. I had a first gen that worked fine with Ubuntu, but I needed to install a fix to get HAL to run correctly so I could mount the new ipod. That worked, but when I went to plug my camera, it was recognized but I got an error that the port was busy and the camera could not be accessed. When I unplugged it all my usb ports froze up. I powered down and rebooted and got the usb ports back, but my camera was still not recognized. Then I tried an ancient card reader. That worked being plugged in and out (with proper ejecting) several times.

Then today I tried to read off the camera card again using the reader. The first time it was fine. The second time the computer did not see the card or reader at all and when I unplugged it my usb ports froze up again. Reboot...I can use my usb mouse and external dvd drive in all of my usb ports (only two), but my camera, card reader, and now ipod are not recognized at all.


My thought at this point is that the fix broke more than it helped. I want to roll back to before I installed it, but I have no idea how. I would say I am a competent user of Ubuntu in a gui and not afraid to use the terminal as long as I have clear directions , but not very knowledgeable about more difficult linux tasks.

If someone could lead me through restoring to before the fix or had another idea to fix this problem, I would be grateful. I need my camera on a daily basis for work, so it has priority over the ipod.

This is the fix I used that I want to undo: [http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/](http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/)

---

### Post by bobpaul on 2007-03-12
> **starchildmom said:**
> This is the fix I used that I want to undo: [http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/](http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/)

Alright, a quick read over the readme and it looks like you just installed all the *.debs from that url you posted? Should be easy to fix. Just install the old versions of the packages.

Let me see... you can use 'apt-cache showpkg PACKAGENAME' to find out versions installed, but I don't think that will tell you what used to be installed.

So, I guess head over to [http://packages.ubuntu.com](http://packages.ubuntu.com) and look up each of the packages you installed from that URL. Ex, by searching "hal-device-manager" I find out the latest version for Edgy is 0.5.7.1-0ubuntu17.

Now you can install a particular version using apt-get like "sudo apt-get install packagename=version" Ex:
```
sudo apt-get install hal-device-manager=0.5.7.1-0ubuntu17
```

Repeat that for all pacakges that you installed. If a package you installed isn't listed in the repositories, uninstall it with "sudo apt-get remove packagename"

Goodluck!

---

### Post by starchildmom on 2007-03-13
Thanks to your instructions I managed to get all the packages uninstalled and learn something new about linux :) It did not, however, fix the problem.

After I posted my original message I tried the ipod again and it worked, but still no camera or card reader. The power light on the card reader did not even light up.. After removing the packages for the fix, the ipod does not work which I expected. Unfortunately, the camera and card reader still do not work either. The card reader power light is lighting up now. The error message i get when I plug in the camera is:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Which is the same message I was getting before the computer stopped acknowledging that I had plugged in the camera at all.

---

