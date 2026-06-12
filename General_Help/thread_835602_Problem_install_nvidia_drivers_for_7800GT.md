---
title: "Problem install nvidia drivers for 7800GT"
date: 2008-06-20
forum: General Help
---

### Post by Trifid on 2008-06-20
[http://forums.overclockers.co.uk/showthread.php?t=17887989](http://forums.overclockers.co.uk/showthread.php?t=17887989)


I installed Ubuntu via Wubi to see how I get on with it and move fully over if it goes well. 

Anyway I have a problem with the drivers. When loading ubuntu the loading bar screen is erroneous where it is stretched and skewed across the screen to about 20 pixels high and leaves the edges of the primary 24" screen. The secondary looks as it does in the link above.

Reconfiguring xserver to go in safe graphical mode I am able to get into a fully working Ubuntu (at the wrong res). Upon rebooting Ubuntu after enabling the full Nvidia drivers I get the Ubuntu brown screen load on the left screen not correctly framed and the PC hangs until I reboot. Repeating results in the same results.

Ubuntu is fully updated.

So errr help? :p

Thanks. :)

---

### Post by lightstream on 2008-06-20
How are you installing the nvidia drivers? I've had problems in the past installing these, till I found the following script:
```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-*
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start
```
Save this script in the same directory as the nvidia driver package, hit Ctrl-Alt-F1 and go to that directory and run it. It should do everything you need to get nvidia working properly. (More notes on [here]("http://www.kuxas.com/38/installing-proprietary-nvidia-drivers-on-ubuntu-linux.html"))

---

### Post by Trifid on 2008-06-20
Was originally doing "sudo apt-get install nvidia-glx-new" which had no effect. When in safe graphical GUI mode it asked me when I try to change my resolution.

---

### Post by lightstream on 2008-06-20
> **Trifid said:**
> Was originally doing "sudo apt-get install nvidia-glx-new" which had no effect. When in safe graphical GUI mode it asked me when I try to change my resolution.

There are other steps you need to do as well as install that package. The script above will take care of all that stuff for you, including making sure you have all required packages and that no other video drivers are installed which could conflict with it. [Read this article]("http://www.kuxas.com/38/installing-proprietary-nvidia-drivers-on-ubuntu-linux.html") for a better description of what it does!

Edited to say: this script is for installing nvidia's own linux drivers, which you can [download from their website]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

---

### Post by Trifid on 2008-06-21
About 3 attempts at that and it worked (kept on returning back to safe graphical mode at 640x480) There was some extra headache getting the right resolution for both monitors set. 

Note to self, do not screw up install. :)

Is there a way to make Ubuntu forget about the secondary screen so it goes into standby/make it more seemless (I use it to chuck windows onto, such as Pidgin or a wanted popup.)

---

### Post by lightstream on 2008-06-21
> **Trifid said:**
> Is there a way to make Ubuntu forget about the secondary screen so it goes into standby/make it more seemless (I use it to chuck windows onto, such as Pidgin or a wanted popup.)

Not sure about that I'm afraid, I only have one screen. Have a look and see if you have the nvidia X-server settings app in Applications > System Tools.

If you do, I think it should give you info about your screens and perhaps some options for configuring dual display.

If you don't have it already, you need to install some package or other - I can try to find the name of that if you need it.

---

