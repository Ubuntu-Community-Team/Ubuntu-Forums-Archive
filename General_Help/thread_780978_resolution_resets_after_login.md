---
title: "resolution resets after login"
date: 2008-05-03
forum: General Help
---

### Post by thorner on 2008-05-03
After upgrading to Hardy, I had problems with my resolution (couldn't get anything higher than 640x480).

I used Alberto Milone's "[EnvyNG]("http://www.albertomilone.com/nvidia_scripts1.html")" script to install the proprietary nVidia drivers, and I now get full resolution (1280x1024).

Unfortunately, my login screen comes up at 1280x1024, but once logged in, it changes to 1152x864. I need to manually (nvidia-settings) bump it back up to 1280x1024. It will then stay at that resolution until I do a reboot. 

This is the resolution line in my xorg.conf under Section "Screen":

...
Option         "metamodes" "1280x1024 +0+0; nvidia-auto-select +0+0"
...

Running 8.04 on AMD64 w/ GeForce 8500GT

A minor annoyance, but any help would be appreciated.

Many thanks!

---

### Post by thorner on 2008-05-06
still doing it....

---

### Post by stream303 on 2008-05-06
Interesting - this is kind of the reverse of the old "desktop screen res ok, but login display isn't".

I'm no xorg expert, but if you'd like to experiment, the way I fixed the changes in resolutions between the two was to use the Virtual option in xorg.conf

Section "Screen"
 Subsection "Display"
 **Virtual 1280 1024**
EndSubSection
EndSection

I left out details, but just make sure that the virtual line is the same as your desired resolution.

Again, not sure if this would help in your case, but it worked for my login screen res problems.

---

### Post by mikehattingh on 2009-03-21
I had this same problem I think. When I set the resolution in System > Preferences > Screen resolution and in System > Administration > Nvidia X server settings the resolution held. Hope this helps.

---

