---
title: "Upgrading to 8800GT"
date: 2008-02-16
forum: General Help
---

### Post by gdp77 on 2008-02-16
Hi to all!!!

My hardware is:

Gigabyte P35-DS3 (Intel P35 chipset)
C2D 6600
Asus 7900 GTX

Ubuntu 7.10 runs great + compiz fuzion (restricted drivers from administration menu ).

I am about to upgrade my graphics card to a 8800 GT, so I have the following questions :

1) Will Ubuntu boot after the upgrade and recognize the card ?
2) If Ubuntu doesn't boot, what should I do ?

Thank u.

---

### Post by Cresho on 2008-02-16
1.  it will probably not boot.
2.  depends on your knowledge.

What I would do is.

1.  uninstall nvidia drivers and run vesa at 640x480 res or 800x600.  after you get your graphics card in this manner, then you can swap.  If you cannot boot into your gdm and access the terminal, then you will have issues.

It is best to have the nvidia driver available.  Prefferably the older driver because the new driver cannot control the fanspeed on the graphics card.  It causes the card to run at full fan speed.  There is no fix to my knowledge at the moment.  also, there is nothing native available that will allow the 8800gt to work properly in ubuntu until the kernel gets updated.

Here is my modified instructions which works great on mines.

------------------------------------------------------------------------------------------
new
on 32bit ubuntu


install dev tools in terminal before proceeding.

1. fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.
2. sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev xserver-xorg-dev
3. uninstall in synaptic nvidia kernel common.  Do a search. apply the changes before exiting synaptic
4. download the driver from nvidia  [http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)
5. log out of ubuntu after download is finished
6. hit ctrl+alt+F1
7. log into your username at the prompt in terminal
8. then in terminal cd /home/yourusername/Desktop
9. ls (just to see if your in the right directory where you downloaded the file in firefox)
10. sudo /etc/init.d/gdm stop
11. sudo sh NVIDIA-Linux-x86-169.04-pkg1.run (ignore the question or say no to kernel download during instal and have nvidia xconfig update the x)
12. "sudo reboot" in the terminal
13. add startup file to system->preference->sessions "nvidia-settings --load-config-only"
14. color correction is under system tools->nvidia x server settings. 1.240 for gamma correction under "x server color correction contrast  4096 sync to vblank"
15. sudo gedit /etc/X11/xorg.conf and add this line to it.

add this to this section "Option         "NoLogo" "true""


Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "NoLogo" "true"
EndSection

16. test in terminal glxgears

old
1. sudo apt-get install nvidia-glx-new nvidia-kernel-common
2. sudo dpkg-reconfigure xserver-xorg
3. add startup file to system->preference->sessions "nvidia-settings -l"
4. add a settings nvidia-settings command into start menu  note:wine does not work too well with antiliasing.

---

### Post by gdp77 on 2008-02-16
From 
[http://www.nvidia.com/object/linux_display_ia32_169.09.html](http://www.nvidia.com/object/linux_display_ia32_169.09.html)

I see that latest drivers are 169.09 which solve the problems you mention (fanspeed etc).

Is there any chance that i could install them BEFORE i make the card swap, so next time I boot everything works fine?

---

### Post by gdp77 on 2008-02-17
Well everything went well!

I made the swap without canging anything in my OS. Ubuntu booted in safe graphics mode (made the change by itself). Then I downloaded and installed envy. Envy did its job perfectly, installing the nvidia drivers. I restarted the system and everything worked perfect!

---

### Post by Cresho on 2008-02-17
glad you found something that worked.  frankly,envy scared me!

---

