---
title: "Screen resolution and wireles card"
date: 2007-07-12
forum: General Help
---

### Post by torben.froberg on 2007-07-12
I have just installed Ubuntu 7.04 on a Lenovo R60 laptop. Everything seems to work almost perfectly, but I have 2 small issues.

1. When I connect the laptop to a LCD screen I would like to increase the resolution from 1024x768 (which is the maximum I can choose in GNOME) to 1280x960, which is the recommended resolution for the screen. How do I configure Gnome to do that? I have tried to change /etc/X11/xorg.conf but it did not have an effect on GNOME.

2, The wireless card is working perfectly, but how do I include it so it start up under the boot process, and not wait until I log in? I have tried to look in the documentation but I haven't found anything useful. Can someone give a link to the proper documentation?

Thanks in advance 

Torben Froeberg

---

### Post by Al3xK3aton on 2007-07-12
Have you tried using a CRT screen instead? It doesn't have a recommended resolution, so it'll look good at 1024x768 if you can't get it to go higher.

---

### Post by ReverendJ1 on 2007-07-12
I think that model laptop uses an Intel Videocard. I had a problem with the resolution on an Intel videocard too (I think I was stuck in 800x600, eh), and 915resolution fixed it for me. Here are some instructions I gleaned off of the Community Documentation from [here.]("https://help.ubuntu.com/community/FixVideoResolutionHowto") :
> Intel Graphics driver (i810) won't use high screen resolutions

There is a common issue with Intel graphics resulting in screen resolutions not being available even after adding them to the xorg.conf file. This happens with the i810 video driver, but the newer intel driver does not have this problem.
Install newer modesetting Intel video driver

Unfortunately the newer driver is only available from 6.10 onwards (Edgy, Feisty etc), but not in 6.06.1 (Dapper). If you have Edgy or above then you can install the newer intel video driver with:-

```
sudo apt-get install xserver-xorg-video-intel 
```

Then edit your /etc/X11/xorg.conf and change the

```
Driver "i810" 
```

to

```
Driver "intel" 
```

You can edit the xorg.conf from the command line using

```
sudo nano /etc/X11/xorg.conf 
```

Alternatively from withing the GUI using

```
ALT+F2 
gksudo gedit /etc/X11/xorg.conf
```

Use 915resolution with the older i810 driver

This problem appears sometimes for laptops with "non-standard"-screen resolution in combination with certain Intel graphic-chips. Background: It seems that the Video Bios (vBios) has to deliver the right resolution for the lcd-screen to enable the autoconfiguration to set this resolution. However sometimes the right resolution is not delivered and consequently the right resolution can not be implemented.

The best fix is provided by the software "915resolution". See i915Driver

You can fix the problem by overwriting the vBios setting in the RAM by using a program called 915resolution. Using 915resolution makes no permanent changes to your computer -- the effects of using it are erased by rebooting.

Here is the description of the 915resolution developer: "915resolution is a tool to modify the video BIOS of the 800 and 900 series Intel graphics chipsets"

To install 915resolution on Ubuntu make sure that you have included the "universe" repository and type (replacing "915resolution" with "855resolution" on Breezy):

```
sudo apt-get install 915resolution
```

Once the program is installed you can use the program to list all available vBios modes:

```
sudo 915resolution -l
```

The result should look similar to:

```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```

If the resolution of your sceen is not present then you can overwrite a unused mode by the value of you screen. Since the results of using 915resolution are temporary you must arrange to have it run each time Ubuntu boots up. This is accomplished by modifying the file /etc/default/915resolution. For example if you want to overwrite the mode 41 by the resolution 2400x1600:

```
sudo nano /etc/default/915resolution
```

Your file should look similar to:

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE  or set to 'MODE=auto'
#
MODE=41
#
# and set resolutions for the mode.
XRESO=2400
YRESO=1600
```

This will ensure that the vBios mode 41 is overwritten in the RAM at boot-time, before initializing the X-windows. Since the resolution is now available in the vBios your system should automatically be able to set the right resolution after rebooting. 


As far as your wireless card coming up on boot, I am not sure if this is the BEST way to do it, but you can make anything run at startup easily. Go to System->Preferences->Sessions and click New. Type in the name (i.e. Wireless start) and then the command you use to bring it up. Easy right?

---

### Post by torben.froberg on 2007-07-12
Thank you. Changing the driver from i810 to intel (and installation of the driver as well) did it. Thank you very much.

Torben

---

### Post by ReverendJ1 on 2007-07-12
Your welcome. I'm just trying to do my part. Did you get the wireless card to come up on boot okay too?

---

### Post by fastpakr on 2007-07-13
> **Al3xK3aton said:**
> Have you tried using a CRT screen instead? It doesn't have a recommended resolution, so it'll look good at 1024x768 if you can't get it to go higher.

What is this drivel?  You've posted over forty times in the last 24 hours with worthless nonsense like the above.  Go find somewhere else to waste people's time.

---

### Post by rookshop on 2007-07-13
Even I use a Lenovo R60. I tried installing the intel driver but I got this message instead.

buzzy@Buzzy-Thinkpad:~$ sudo apt-get install xserver-xorg-video-intel 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libseda-java libcommons-cli-java libgtk-jni libcairo-java
  libbcprov-java libglib-java libgtk-java
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-video-i810
The following NEW packages will be installed:
  xserver-xorg-video-intel
0 upgraded, 1 newly installed, 1 to remove and 87 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by Wim Sturkenboom on 2007-07-13
> **Al3xK3aton said:**
> Have you tried using a CRT screen instead? It doesn't have a recommended resolution, so it'll look good at 1024x768 if you can't get it to go higher.So now I must carry a laptop AND a CRT. Quite defeats the object in my opinion.

---

### Post by ReverendJ1 on 2007-07-13
@rookshop - It appears your downloads directory is locked by something else. Try rebooting and installing again.

---

### Post by rookshop on 2007-07-14
I rebooted and completed the installation. I also modified the xorg.conf file. But the desired resolutions are still not available in the screen resolutions window. :(

---

### Post by ReverendJ1 on 2007-07-14
Did you try using 915resolution to overwrite an unused resolution? It is different than editing the xorg.conf file.

---

### Post by rookshop on 2007-07-14
Yeah, but now I get another option of "1280x1280" in my resolution window. Its very strange and I have never seen this resolution being used before.

---

