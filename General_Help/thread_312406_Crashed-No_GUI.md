---
title: "Crashed-No GUI"
date: 2006-12-04
forum: General Help
---

### Post by dontgetshocked on 2006-12-04
I managed to crasg ubuntu. I un-installed my glx drivers and now I dont have a gui after the boot, just a text prompt for username and password and then just a prompt again.  I tried using the restore but it did not fix anything. What else can I do?

---

### Post by taurus on 2006-12-04
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dontgetshocked on 2006-12-04
When do i input this code? at the prompt after username and login?

---

### Post by taurus on 2006-12-04
After you've logged in with your username & password.

---

### Post by dontgetshocked on 2006-12-04
It says that server is broken or not fully installed
After running the below command

sudo dpkg-reconfigure xserver-xorg

---

### Post by taurus on 2006-12-04
```
sudo aptitude update
sudo aptitude install xserver-xorg
```

---

### Post by dontgetshocked on 2006-12-05
I am 0 for 0. Code executed with no errors but still no gui.
I am still left with a command line after login and password.
Anything else I can try?

---

### Post by gary101 on 2006-12-05
After everything mentioned above did you put the command 'startx' at the command prompt?

---

### Post by dontgetshocked on 2006-12-05
Yes, I did but it gave me something strange about a enlightenment desktop and it had no visible things to click on, unusable!
Stay with and help me work thru thus please.

What next?

---

### Post by gary101 on 2006-12-05
I am not an expert at this, but I had similar problems after uninstalling drivers

First thing I did was to re-install the drivers from the command prompt, then carry out the steps you have tried. Everything worked out ok.

I don't know what graphics card you are using so I can't help you with the right drivers from the command line but you should find the instructions somewhere in the forum.

If you let me know what graphics card you have I would be happy to see if I can find any info for you.

---

### Post by dontgetshocked on 2006-12-05
Nvidia FX 5600 Ultra 256 mb

---

### Post by gary101 on 2006-12-05
Ok try this at the command prompt:

sudo aptitude install nvidia-glx nvidia-kernel-common linux-restricted-modules-`uname -r` (all one line)

Then
sudo nvidia-xconfig

Then startx

Let me know how it goes, any errors etc

---

### Post by dontgetshocked on 2006-12-05
Do you want the good news or the bad news first?
There were no errors but still left at the command prompt
Of course I did forget to use the startx command which last time brought me into something called enlightenment which was of no use at all.
I will in a while shut down and swap drives again and try the start command and see what happens.

Will let you know

Thanks,

---

### Post by fragos on 2006-12-05
How did you uninstall the driver?  Did you use Synaptic and the Ubuntu repositories?

---

### Post by dontgetshocked on 2006-12-05
Yes, I used synaptic to un-install

---

### Post by fragos on 2006-12-06
On a working system using Synaptic to install nvidia-glx should be all you need to do -- worked for me with FX5200.  When a GUI fails to start it can be that /etc/X11/xorg.conf has reference to a non existent driver.  Without a 3D diver Ubuntu would assign diver "nv" which has open source 2D support.  The 3D driver would be called "nvidia".  The most generic driver is "vesa" and should work with anything.  Both vesa and nv are part of the Ubuntu install.  Perhaps looking at xorg.conf to insure vesa or nv is selected will fix things for you.

---

### Post by RAOF on 2006-12-06
I'd suggest installing the **ubuntu-desktop** package, to get all the default programs installed again.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

After that, a restart (or running **sudo /etc/init.d/gdm start**, which will start up the GUI) should get you back to the GUI.

---

### Post by dontgetshocked on 2006-12-06
Well, I am up and running after successfully installing the nvidia driver.
I also had to do a start and a re-start of the desktop for it to start.
The graphics are not quite right though, it scrolls the screen when you try to click or scroll down, not smoothly as before.
Am scared to try anything at this point else, maybe when i re-boot all will not be well.

It shows up the glx in synaptic but still the graphics do not perform as they should.


Suggestions?


Thanks again for ALL your help.

---

