---
title: "Backing out latest NVIDIA driver"
date: 2015-03-23
forum: General Help
---

### Post by RayDeCampo on 2015-03-23
I have been having some issues with the 304.125 driver installed from the Ubuntu repositories (14.04) and I was considering trying downloading the latest driver from NVIDIA to see how that works out.

The thing is, the last time I tried a later driver with this system (from the repositories) the driver did not agree with the system at all and I had to jump through a bunch of hoops and effort to get back to where I had been with 304.125.  So this time I want to be prepared and know what needs to be done to restore 304.125 before I install the latest NVIDIA driver.

So, assume I installed a new driver from NVIDIA and my system is not working properly - how do I restore the 304.124 from the repositories?  (Assume I have command line access, I was able to get there last time.)

---

### Post by efflandt on 2015-03-24
What video card do you have and what issues are you having with that driver? I have a GTX 750 Ti with the new Maxwell chip and although it worked in 14.04.1 live/install iso, apparently nouveau did not support it in the installed system (could not even get login gui), and after I installed **nvidia-current** (some 304 version) from a recovery boot, that did not support it either according to logs (I got to gui login, but still X would not start). So I purged that and installed **nvidia-331-updates** and that worked.

It is generally recommended to use Ubuntu packages rather than the script right from nvidia.com because then everything should work together and update automatically. But if you want something even newer than what is available in the normal repos, there are other ppa's like xorg-edgers ppa that can be added. I am currently using **nvidia-346** package (currently 346.47) from there. It does not seem to be any faster than nvidia-331-updates by default, but I wanted to play around with video overclocking which requires 337 or newer drivers.

Anyway if you want to try most recent nvidia drivers from standard repos, you could boot to the login screen, but don't log in. Press Ctrl+Alt+F1 to go to text console, log in there, then do:```
sudo apt-get purge nvidia*
sudo apt-get update
sudo apt-get install nvidia-331-updates
sudo reboot
```If you have not used sudo before, when it asks for your password, just blindly enter your normal login password (no characters will appear). See how that works. If you want to go back to the 304 version, just do the same as above, but install **nvidia-current** instead of nvidia-331-updates.

If you have any trouble with weird scrolling in Firefox, etc. install **CompizConfig Settings Manager** (which you can do from Software Center) then open that and under Utilities > Workarounds and check **Force full screen redraws (buffer swap) on repaint**.

---

