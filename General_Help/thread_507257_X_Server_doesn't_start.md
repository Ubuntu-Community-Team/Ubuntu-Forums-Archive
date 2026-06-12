---
title: "X Server doesn't start"
date: 2007-07-22
forum: General Help
---

### Post by TechedRonan on 2007-07-22
After I've installed the NVidia drivers(from Nvidia.com) it works just fine until I reboot, then I get an error message saying that the X Server can't start and after that I get to a console where I can login.

So this is what I do after installing Ubuntu:
1. Download and Install latest updates, then download the NVidia drivers from NVidia.com
2. Download and install libc6 since nvidia requries that.
3. I press CTRL+ALT+F2(This is what I get when trying to boot)
4. I write: "sudo /etc/init.d/gdm stop"
5. And then: "sudo sh /home/deruu/Desktop/NVIDIA-Linux-x86-100.14.11-pkg1.run", and let it install..
6. I let the installer modify the xorg file
7. After the installer is complete I write "sudo /etc/init.d/gdm start" and login.
8. I enable desktop effects and those work just fine.
9. I reboot, and this is where I am now.

xorg.0.log:
[http://upl.vs-hs.com/download/8d771478a006bd0fcaac5cb3f1775d89](http://upl.vs-hs.com/download/8d771478a006bd0fcaac5cb3f1775d89)
xorg.conf:
[http://upl.vs-hs.com/download/f2cad766f4cdc885c78f4eef30cd21f7](http://upl.vs-hs.com/download/f2cad766f4cdc885c78f4eef30cd21f7)

---

### Post by DIESELMACHINE on 2007-08-05
Hi. I have the same problem. Can anybody help me please?

---

