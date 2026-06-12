---
title: "How to install Nvidia drivers"
date: 2007-04-14
forum: General Help
---

### Post by geovino on 2007-04-14
How do you install Nvidia drivers? I see that I have Nvidia settings on my Applications menu but it doesn't have an option to install the drivers. Maybe they are already installed? Except when I try to use Google Earth it does not work.

Any clues?

---

### Post by rocknrolf77 on 2007-04-14
If you set your ubuntu version in your profile it's much easier to help you. :)

---

### Post by tommcd on 2007-04-14
See this page by nvidia guru tseliot to install nvidia drivers on any version of ubuntu:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)
No matter if you are on breezy, dapper, or edgy, use method 1. It is the easiest and will likely work fine. Don't install nvidia's drivers from the nvidia website (method 2 in the guides) unless nvidia-glx (method 1) does not work.
See this for the quick and easy way on edgy:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)
and dapper:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)
Hope this helps.

---

### Post by Maestro23 on 2007-04-14
Nvidia Drivers:

Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by geovino on 2007-04-14
using version 6.10

---

### Post by r4ik on 2007-04-14
Try the envy script suggested by Maestro23

Good luck !

---

### Post by x1a4 on 2007-04-14
Hi,

download the driver from nvidia.com, then: 

logout, then 

Ctrl+Alt+F2

login as yourself, then 

stop gdm: 

sudo /etc/init.d/gdm stop

then

run the driver installer: 

sudo sh /path/to/nvidia/driver.sh 

follow the installer prompts, then 

start gdm: 

sudo /etc/init.d/gdm start

and you're done. :)

---

### Post by geovino on 2007-04-16
Thanks for all the info, but my screen is very sharp and clear with what ever drivers were installed when I initially installed Edgy. Everything works but Google Earth and it's not an important program anyway. I can get all the map views from regular Google maps which is about the same as Google Earth.

Maybe when I upgrade to Feisty it will handle Nvidia better than it does now. 

Thanks again.

---

