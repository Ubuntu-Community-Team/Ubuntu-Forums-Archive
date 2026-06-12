---
title: "Newly installed Ubuntu 12.10 can't change brightness"
date: 2013-02-25
forum: General Help
---

### Post by Ax More on 2013-02-25
I installed Ubuntu 12.10 on my laptop.
But brightness can't be changed.
I've tested all additional drivers for graphic card.
Graphic info is unknown in "System Detail".

And I've tried installing Official driver from Nvidia, using "sudo service lightdm stop" and "sudo sh Nvidia-XXX-XXX-XXX.run". Installation failed.

My graphic card is Nvidia GT425M.
And laptop is LG XNOTE A505.

Do you guys have some ideas?
:popcorn:

---

### Post by Toz on 2013-02-25
Hello and welcome to the forums.

A couple of suggestions:

1. With the nvidia proprietary driver installed and activated, you could try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device Section of **/etc/X11/xorg.conf**. This has been known to fix brightness issues in some laptops with proprietary nvidia cards.

2. Try to identify your valid backlight interface. The backlight interfaces are located at /sys/class/backlight - each interface with its own directory (ideally you should only have one, but occasionally there are more). Within that directory, there are a number of files:
- actual_brightness = the current brightness value
- max_brightness = the maximum allowable brightness value
- brightness = the brightness set file

You can test each interface by echo'ing in a value between 0 and the contents of max_brightness to test if that interface is valid:
```
echo VALUE | sudo tee /sys/class/backlight/INTERFACE/brightness
```
...where VALUE is a numberic value between 0 and the max_brightness and INTERFACE is the directory name. 

If you have more than one interface, and one of the interfaces works via the process above, using the **acpi_backlight=vendor** kernel boot parameter may help.

Reference links:
- [Backlight Wiki]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight")
- [Kernel Boot Parameters Wiki]("https://wiki.ubuntu.com/Kernel/KernelBootParameters")

---

### Post by danielda on 2013-02-26
> **Toz said:**
> Hello and welcome to the forums.

A couple of suggestions:

1. With the nvidia proprietary driver installed and activated, you could try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device Section of **/etc/xorg.conf**. This has been known to fix brightness issues in some laptops with proprietary nvidia cards.

2. Try to identify your valid backlight interface. The backlight interfaces are located at /sys/class/backlight - each interface with its own directory (ideally you should only have one, but occasionally there are more). Within that directory, there are a number of files:
- actual_brightness = the current brightness value
- max_brightness = the maximum allowable brightness value
- brightness = the brightness set file

You can test each interface by echo'ing in a value between 0 and the contents of max_brightness to test if that interface is valid:
```
echo VALUE | sudo tee /sys/class/backlight/INTERFACE/brightness
```
...where VALUE is a numberic value between 0 and the max_brightness and INTERFACE is the directory name. 

If you have more than one interface, and one of the interfaces works via the process above, using the **acpi_backlight=vendor** kernel boot parameter may help.

Reference links:
- [Backlight Wiki]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight")
- [Kernel Boot Parameters Wiki]("https://wiki.ubuntu.com/Kernel/KernelBootParameters")

This fixed my issue, many thanks! I was seeing the same thing, 100% brightness no matter what GUI settings. Mine was on a Macbook Air 3,1 (11"), Linux Mint 14, NVIDIA 313.18. My power consumption has almost halved. 

Edit: should just add, my xorg.conf was in /etc/X11/xorg.conf.

---

### Post by Toz on 2013-02-26
Glad to hear it worked for you. 

> Edit: should just add, my xorg.conf was in /etc/X11/xorg.conf.
Thanks for the catch. I've corrected my original post.

---

