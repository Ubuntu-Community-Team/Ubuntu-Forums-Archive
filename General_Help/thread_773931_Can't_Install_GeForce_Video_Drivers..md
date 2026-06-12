---
title: "Can't Install GeForce Video Drivers."
date: 2008-04-29
forum: General Help
---

### Post by FredJones on 2008-04-29
I have a new HP machine, running Ubuntu 7 beautifully, with Gnome. I purchased and popped in there today a GeForce 8400 GS video card and rebooted. I get a command line and starting Gnome and/or X both fail. So I tried the instructions here [http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html) but when I run this file it says I am missing libc headers. So I did "aptitude install libc" and that ran fine. 

When I run the nvidia install app however, it says that same thing.

Can someone point me in the right direction here? Perhaps I am going about this the wrong way...

Thanks.

---

### Post by pedro_orange on 2008-04-29
So can you not get a GUI at all?

Otherwise I'd say use Restriced Drivers (System>Admin>Hardware Drivers)

Other than that you could wget the driver you need and then install it from terminal (Ctrl+Alt+Fx)

---

### Post by FredJones on 2008-04-29
> So can you not get a GUI at all?

That's right. startx gives me a whole screen of text and at the bottom says Fatal error. no screens found.

PS: I am a newbie to Linux...

---

### Post by ryanhaigh on 2008-04-29
Press ctrl-alt-f1 to take you to a terminal, login using your normal details, then use 
```

sudo apt-get install nvidia-glx-new

```
The this
```

sudo nvidia-xconfig

```
To tell the system to use the newly installed driver.

Then this
```

sudo /etc/init.d/gdm restart

```
To restart the GUI system and hopefully you will be good to go.

As with all softare in Ubuntu/Linux it is better to use the drivers available in the repos. The normal procedure for installing nvidia drivers is much simpler but this should work.

Check this out if you have any further problems, or post back here.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by FredJones on 2008-04-29
Fantastic, that did it!

BUT, when I plug in a second monitor, Ubuntu doesn't seem to see it. I tried plugging in two monitors (both of which of course work fine on another PC) and it boots into the VGA one and in System-Administration-Screens and Graphics it only shows one screen.

So I unplugged the VGA one and left just the digital (or whatever it is) screen plugged in and restarted. It booted into that screen alone.

How can I get both screens to work?

Thanks!

---

### Post by ryanhaigh on 2008-04-29
The nvidia driver comes with a configuration application that always works for me. Just press alt-f2 to bring up the run application dialog then enter nvidia-settings. If you want to make these changes permanent use gksudo nvidia-settings enter your password and when you have things configured the way you want press the save to x configuration file.

As a side not I recommend using twinview for a dual monitor setup with compiz (desktop effects in system>prefs>appearance) enabled.

---

### Post by FredJones on 2008-04-29
Yes, I found [https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors) just after I wrote last. But whatever I try to set to show both monitors (whether twinview or separate x screen) it says "Failed to set Metamode"

I just want one screen next to the other--a normal, simple layout. :)

I can't yet get the second one to work at all. :(

Any other ideas?

---

### Post by ryanhaigh on 2008-04-29
[http://ubuntuforums.org/showthread.php?t=690580](http://ubuntuforums.org/showthread.php?t=690580)

The OP in this thread had the same issue but determined it was due to a poorly configured xorg.conf. Reconfiguring x using ```
sudo dpkg-reconfigure xorg.conf
``` using defaults for everything but the driver (use nvidia not nv) worked for them, they could then use nvidia-settings to configure the graphics as desired.

It is always a good idea to backup your /etc/xorg.conf file once you have it working and want to try something new.

---

### Post by FredJones on 2008-04-29
Running "sudo dpkg-reconfigure xserver-xorg" (which is what he used) indeed worked. Well, I had to restart afterward and THEN nvidia-settings worked. :)

Thank you very much!!!!

---

### Post by Nunu on 2008-04-29
You might also consider trying the Nvidia-New driver if you have problems with using Compiz and Emerald. I know that using the Nvidia-New driver allows you to use the settings app to configure the second screen and save the config to the XORG file. Usually when I do a fresh install i install the Nvidia-new, then reboot the machine. At this point only the primary screen will come on. go to a terminal and enter nvidia-settings then configure the screen restart X (ALT + CNTRL + Backspace) and all should be fine and dandy even worked on 8.04

---

### Post by milind4 on 2008-04-29
> **ryanhaigh said:**
> Press ctrl-alt-f1 to take you to a terminal, login using your normal details, then use 
```

sudo apt-get install nvidia-glx-new

```
The this
```

sudo nvidia-xconfig

```
To tell the system to use the newly installed driver.

Then this
```

sudo /etc/init.d/gdm restart

```
To restart the GUI system and hopefully you will be good to go.


will this work in hardy heron too? I have to install drivers for Nvidia Geforce 6150 LE, and being a noob, I'm stumped...

---

### Post by Nunu on 2008-04-29
You can go to synaptic package manager. You will need to add some repositories and then reload refresh synaptic. Once you did this you can simply highlight the software list and then type nvi and it should display all the nvidia software available. I did notice in that in Hardy i needed to install the settings console separately.

---

### Post by milind4 on 2008-04-29
I have already downloaded a Linux driver package from the Nvidia site. It says I need to run it as root with Xserver closed
 I closed xserver and i got a black screen with a couple of lines of text and then a blinking cursor. what exactly am i supposed to do here? when i enter in the command that nvidia has told me to eneter, nothing happens.

---

### Post by Nunu on 2008-04-29
Bump 

I would suggest rather running the driver found in Synaptic. I have had very little success with the drives from the nvidia site.

---

### Post by FredJones on 2008-04-29
Presently it seems to be working. I also don't actually know what's Emerald nor Compiz are. :)

Thanks.

---

### Post by Plasma_NZ on 2008-04-29
Ok seen heaps of problems people are havin with nvidia drivers and installing them...  

I've used the below method for my multi-screen setup, and its working flawlessly - check my other posts about my setups..

will add my 2cents and try and help here..  My little guide assumes your already in a X - if not disregard step 1.


```
1. In ubuntu press "ctrl + alt + F1"
2. Login to your user account (not root)
3. sudo /etc/init.d/gdm stop (will as for root password)
4. cd /home/account_name/Desktop  (or where u downloaded the driver 2)
5. sudo sh NVIDIA_DRIVER_PACKAGE_NAME
6. Follow directions from installer
7. once done... type "startx" to boot back into GUI 
8. in terminal type "sudo nvidia-settings" and configure accordingly to your liking..
```

---

### Post by ryanhaigh on 2008-04-29
Installing the nvidia driver from the nvidia website it NOT the reccommended method. Whenever the kernel gets updated the user is going to be left with an incompatible driver module and X won't start. Breakage such as this generally leaves a bad impression of ubuntu and linux, in reality this is unreasonable. 

As with all software in Ubuntu and other Linux distros it is recommended to use the packages provided in the software repositories, this is even more important for drivers for the reason mentioned above. The restricted driver manager has been included for a couple of releases to deal with issues such as installing the nvidia driver. Using that is the easiest method of installing the driver, in this instance the OP didn't have a GUI to use the restricted driver manager. Knowing that the recommended driver for Geforce 8 series cards is nvidia-glx-new (**Nvidia-new**) this is why I directed him to use that package.

Please before recommending that people use drivers from outside the ubuntu repos, ensure that they have at least tried the recommended methods fist.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Personally I think an ubuntu/insertdistrohere should suggest to nvidia that they at least provide a suggestion to use your distros package manager to install the driver as many other software developers do.

---

### Post by Nunu on 2008-04-29
> **FredJones said:**
> Presently it seems to be working. I also don't actually know what's Emerald nor Compiz are. :)

Thanks.

Compiz is a program that adds nice little gimicks like Glass borders and the Cube and Window wobble. Emerald is a theme manager that allows you to change the look of your windows. There is a few that makes it look just like Vista.

---

