---
title: "USB udev rule accepting only one Environnement Variable"
date: 2021-01-16
forum: General Help
---

### Post by pidou66 on 2021-01-16
hello,

I'm on Ubuntu 18.04.5 LTS and I wrote a usb udev rule to execute a script when someone unplug a USB device from my computer.

here it is:

```
ACTION=="remove", ENV{DEVTYPE}=="usb_device" , ENV{ID_MODEL_ID}=="c019" , RUN+="/bin/su jensen -c '/home/jensen/Documents/2script.sh'"


```

the problem is that with the 2 ENV{variable}, the script isn't executed. 

if I remove the "DEVTYPE" variable, the rule works but execute the script 2 times. 
if I remove the "ID_MODEL_ID" variable, the script is executed one time but with any USB device removed. 

Why can't I have those two environnement variables at the same time ?

---

