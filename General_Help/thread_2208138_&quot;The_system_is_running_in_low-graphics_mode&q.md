---
title: "&quot;The system is running in low-graphics mode&quot; error"
date: 2014-02-26
forum: General Help
---

### Post by dimitri6 on 2014-02-26
Hi all.

I have a fatal issue with my Ubuntu 13.10 and I would appreciate any assistance I can have. Upon login I'm presented with "The system is running in low-graphics mode" error and when I select OK, the screen goes black with nothing more to do.

[IMG]http://i.stack.imgur.com/AiwJH.png[/IMG]

Situation:  The system was running smooth and perfectly like a champ with no issues whatsoever.  But yesterday, the little devil in me was trying to convince me to switch to Gnome 3.10.  I then installed Gome 3.10 and 9 times out of 10 the desktop was crashing when I was attempting to search the applications.  After some reading in this forum, that issue is apparently caused by the nVidia graphic drivers and many suggested removing and re-installing the graphic drivers.  I then removed and re-installed the nVidia graphic drivers.... and upon reboot, I first saw this dreaded message: "The system is running in low-graphics mode" error.

I then rebooted in recovery mode and completely uninstalled both Gnome 3.10 and nVidia drivers.

I rebooted to Unity with the "Nouveau" drivers at a ridiculously low resolution of 640x480 that can't be changed. At least, I was able to login to Ubuntu Unity.

I went to the "Additional Drivers" tab, and selected the latest proprietary nVidia driver v331.
I rebooted and got the "The system is running in low-graphics mode" error
I then booted to the Recovery Root Terminal, uninstalled nvidia drivers (sudo apt-get remove --purge nvidia-*)

Rebooted to the Nouveau 640x480 Unity and selected a previous version 304 proprietary nVidia driver.
I rebooted and I keep on getting the "The system is running in low-graphics mode" error.

I spent more than 6 hours (from another computer) reading the forums and googling on this issue and tried almost everything. (rebuilding linux headers, etc, etc) To no avail.

I tried all these steps:
[How to install Nvidia drivers in Ubuntu]("http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html")
[How to manually install Nvidia drivers in Ubuntu]("http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html")
[How to fix &#8220;The system is running in low-graphics mode&#8221; error]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error")
[How to uninstall a nvidia driver completely]("http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely")

With the proprietary Nvidia drivers I keep on getting the same "The system is running in low-graphics mode" error and the black screen.  The only way to login to Ubuntu is to completely purge the nvidia drivers and use the Nouveau driver at 640x480 resolution.

This is how my desktop looks like with the Nouveau driver: Notice the 4:3 640x480 on my LG 23" W2353V widescreen monitor and broken white menus. (at least I can access the system to get the Nvidia drivers)
[https://www.dropbox.com/s/amwbvcp0ygfvfmr/nouveau.png](https://www.dropbox.com/s/amwbvcp0ygfvfmr/nouveau.png)


Question:

Is there any way I can restore Unity the way it was before with the nVidia drivers?

My system is a Lenovo Core2 Duo, Ubuntu 13.10 with a nVidia GeForce 9800 GT PCIe graphics card.

I'm confident I won't have to do a complete OS reinstall just for a display issue.

Thank you in advance for any suggestions!

---

### Post by Bashing-om on 2014-02-28
dimitri6; Well,

As a thought:
When you do "sudo apt-get remove --purge nvidia-*" :
above command will also remove the nvidia-common package and the nvidia-common package has as a dependency the ubuntu-desktop package.
So after above command you should also give the installation command for ubuntu-desktop package:
```

sudo apt-get install ubuntu-desktop

```
You also might have to move a custom xorg.conf created by the driver or yourself:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-old

```
To insure the open source driver gets installed !
```

sudo apt-get install xserver-xorg-video-nouveau

```

Before rebooting, make sure nouveau isn't blacklisted:
```

cd /etc/modprobe.d/
ls

```

[INDENT]understanding what goes on with graphics driver.
[INDENT][INDENT][INDENT]can get real deep !
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by evan8 on 2014-02-28
I know this happened to me once on my laptop when i activated one of ubuntu drivers when they promted me to do so. My only fix was clean in stall. I know that doesn't help you much .

---

### Post by jeanjd63 on 2014-03-01
Hello

You can try :
[B]sudo  apt-get  purge  "nvidia *"
sudo  apt-get  install  nvidia-current
sudo  reboot[/B]

---

### Post by grahammechanical on 2014-03-01
At any point did you select Nouveau in Additional Drivers? When we are in Recovery Mode the Resume option loads llvmpipe which uses the CPU to render accelerated commands and not the GPU. It is fine as a fallback mode for systems with a graphic adapter that cannot do 3D rendering in hardware but it is not what we are used to if we have a more powerful GPU.

Using Additional Drivers to install a proprietary video driver will de-activate Nouveau and activating Nouveau in Additional Drivers will uninstall the proprietary video drivers. In my opinion this is a less messy way of making these changes.

Regards.

---

### Post by dimitri6 on 2014-03-03
Thank you all for the replies.  I tried all these solutions before but none worked.

Ever since I posted here, the next day I ended up doing a clean install (home folder intact) and now the system works great.

---

### Post by Bashing-om on 2014-03-04
dimitri6; Hey,

(RE-)install is always one sure fired fix !

Please mark this thread as solved: 1st post -> thread tools

[INDENT]keep on keep'n on
[/INDENT]

---

