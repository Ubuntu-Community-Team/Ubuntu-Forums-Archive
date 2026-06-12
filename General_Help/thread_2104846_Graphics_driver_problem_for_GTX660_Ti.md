---
title: "Graphics driver problem for GTX660 Ti"
date: 2013-01-14
forum: General Help
---

### Post by MDJPster on 2013-01-14
In the "additional drivers" section of Software Sources it says there is  no proprietary drivers in use. I can't seem to find another way to  install them, other than downloading them directly from nVidia and  installing them myself (which always breaks my system, forcing me to  reinstall). I can't even seem to find the Nouveau driver though.  

I didn't have this problem with my GTX570.
  

I am looking for drivers since there is stutter going on in the  desktop animations and Steam "Big Picture" mode results in just a black  screen.
  

I used the command:[INDENT]   *sudo apt-get install nvidia-current nvidia-settings*
 [/INDENT]Now I have Nvidia x-server as an app in my list, but still saying I'm not running any proprietary drivers.
  

Also, I have two monitors, and when I set it to "Mirror displays" it  dropped my resolution to 1024x768 (4:3) and wouldn't let me restore to  my previous setting. Before I ticked "Mirror displays" the resolution box already said  1024x768 (4:3) but it looked more like 1920x1080 (16:9). A reboot, following a system lockup not long after the change in settings, fixed this, but I'm sure if I change anything in the "Displays" menu this will happen again.


I am running Ubuntu 12.10 64bit with the latest version of GNOME + GDM (this was also an issue with Unity, however).
  

My graphics card is an EVGA GTX660 Ti FTW+ (3 GB RAM) plugged into an ASRock Z77 Pro 3 motherboard.

---

### Post by grahammechanical on 2013-01-14
When Additional Drivers says 'there are no proprietary drivers in use' it means that you are using the open source Nouveau driver. It is the default driver.

Did Additional Drivers give you a list of drivers? It usually gives a list of four - three proprietary drivers and Nouveau.

We are able to select a driver and click apply. What is your situation?

Regards.

---

### Post by MDJPster on 2013-01-14
No, it says "No proprietary drivers in use" and the box above it is greyed out. I tried installing Jockey from USC (since 12.10 doesn't use it anymore) and it's not even showing up in my apps.

---

### Post by MDJPster on 2013-01-14
I'm uploading two screenshots:
First is "Additional Drivers" tab in Software Sources and the second is an error message I get every time I log on since the resolution+aspect ratio change. My custom GNOME theme doesn't work until I close this message.

---

