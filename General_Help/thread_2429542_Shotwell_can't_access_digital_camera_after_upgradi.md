---
title: "Shotwell can't access digital camera after upgrading to Ubuntu 19.04"
date: 2019-10-19
forum: General Help
---

### Post by duane3131 on 2019-10-19
When I upgraded from Ubuntu 18.04 to 19.04, Shotwell couldn't access my Cannon camera. I got the warning: The camera is locked by another application.

I found that the camera was automounted by gphoto2. I have to manually unmount the camera before I can access it with shotwell.

Under Settings - Removable Media, I have Shotwell as the default for handling photos.

My wife's computer, still running Ubuntu 18.04, has no problem accessing my Cannon camera.

In Ubuntu 19, is there a way to not automount my camera, while still allowing automounting of USB sticks?

Thanks for your help!

---

### Post by TheFu on 2019-10-19
Is the shotwell program a snap package or a normal package?  Snaps have many more constraints and what you've described should like a snap package constraint.

---

### Post by duane3131 on 2019-10-22
I have had the shotwell program on my PC since I got my camera in 2013. I'm guessing it is a normal package. I've upgraded Ubuntu versions every time a new version came out. Everything worked with Shotwell untill I upgraded to Ubuntu version 19.04

---

### Post by Frogs Hair on 2019-10-23
Shotwell is a .deb and shows no snap dependency. The upgrade could have affected the application, but I don't know how. 

> [COLOR=#000000]In Ubuntu 19, is there a way to not automount my camera, while still allowing automounting of USB sticks?[/COLOR] Do you use a USB cable to connect the camera ?  My camera is detected as another USB and does not affect the addition of another device.

---

