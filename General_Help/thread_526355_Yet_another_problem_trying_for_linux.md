---
title: "Yet another problem trying for linux"
date: 2007-08-15
forum: General Help
---

### Post by rdbaron02 on 2007-08-15
I just finished installing Wubi Ubuntu, and right as ubuntu loads up. I get this message "Failed to start the X server (your graphical interface).   It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose thet problem."  

I can select Yes.

I follow a one way path of yesses, and new questions.

The final message i get is "The X server is now disabled.  Restart GDM when it is configured correctly."

Then i am taken to a screen that is showing everything is starting ok. and the last line says *running local boot scripts (/etc/rc.local)
I can type commands from a blinking dash
Please help me figure this out, this is my 3rd failed attemt!!!! :(

---

### Post by rdbaron02 on 2007-08-15
Also, I have a Nvidia 8400M GS 128mb video card

---

### Post by rdbaron02 on 2007-08-15
I have been reading through the forums, and i ended up booting in recovery mode and logging in as root.

now.....
what command do i type in?

---

### Post by Steve1961 on 2007-08-15
I'm not familiar with wubi, but you need to edit the xorg.conf file.

nano /etc/X11/xorg.conf

Find the section that looks similar to this:

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"


and change the nvidia entry to vesa.  Save the file and reboot:

shutdown -r now

Note: unless you have a setup a root accound preface all commands with sudo

---

### Post by rdbaron02 on 2007-08-15
WOO HOOO!!!!! im finally in linux. what command would make available more resolutions.

Because, under system<preferences<screen resolution, i only have 800x600 and 640x480 resolutions available

---

### Post by Steve1961 on 2007-08-15
> **rdbaron02 said:**
> WOO HOOO!!!!! im finally in linux. what command would make available more resolutions.

Because, under system<preferences<screen resolution, i only have 800x600 and 640x480 resolutions available


That's because you only have the basic vesa driver running. Now you need to install the nvidia driver (search for the many how tos on this forum).  If it goes wrong, just revert to vesa and try again.

---

### Post by rdbaron02 on 2007-08-15
I read the howtos, but i when i go to system>administration>restricted drivers manager.

It says "your hardware does not need any restricted drivers"

What do i do to get that driver installed?

---

### Post by distroman on 2007-08-15
You could either try envy-
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
I have never used it myself but seems people are happy with it.

Or have a look here-
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

---

### Post by Steve1961 on 2007-08-16
Or just try:

sudo apt-get install nvidia-glx-new

Then edit xorg.conf and change the vesa entry to nvidia.  Reboot.

---

### Post by ZipoTe on 2007-08-16
I always downoald the official drivers from nvidia website. There you can follow the instuctions and you will have the latest drivers :)

---

### Post by hikaricore on 2007-08-16
Many of the 8xxx series cards are not supported by the driver included in the Restricted Manager (to the best of my knowlege this driver has not been updated to the 100 series).

The 100.x.x series of the driver which can be installed via envy or from the official NVIDIA website is your best bet for these cards.

---

