---
title: "Graphic support problem in dual boot with windows10"
date: 2015-11-21
forum: General Help
---

### Post by abishek3 on 2015-11-21
Recently after i had dual booted my UEFI firmware device to ubuntu, i did a graphic update from windows side and as from that time im coming across this problem in ubuntu side and none of the options in that error helps to rectify. Can anyone help me out with what the actual problem is please,,????

ERROR:
"Your screen,graphic card and input device settings bot detected correctly.you will need to configure this yourself."

---

### Post by lisati on 2015-11-21
*Thread moved to **General Help**.*

---

### Post by oldfred on 2015-11-21
What video card/chip?
You may need to install proprietary graphics driver for your model video card.

If you installed one before make sure to totally purge old one, or you will have conflicts.
Easiest to just use System settings, software updates.

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 

   #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q
xrandr --q1
#What is installed
dkms status

---

