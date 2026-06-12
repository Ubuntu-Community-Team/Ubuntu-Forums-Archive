---
title: "Does Bumblebee work with 12.10?"
date: 2012-10-19
forum: General Help
---

### Post by mushypeas on 2012-10-19
I have one of those Nvidia/Intel combined cards and need bumblebee to get unity 3d working. Does bumblebee work with 12.10 please?

---

### Post by xangoch on 2012-10-20
same problem,need some help...

---

### Post by titusjaka on 2012-10-20
Hi, guys!
You need a little effort to resolve this issue.
The answer was found here: [ click me!]("http://askubuntu.com/questions/202644/how-to-install-nvidia-optimus-driver-on-ubuntu-12-10")
You have to execute this commands:
```
sudo apt-get install ppa-purge
sudo apt-get purge bbswitch-dkms bumblebee-nvidia
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get upgrade ; sudo apt-get dist-upgrade
sudo apt-get install bumblebee bumblebee-nvidia
sudo reboot
```
That's all! My Bumblebee works now and battery doesn't run out so quickly.

I hope this answer will be helpful for you as much as for me!

---

### Post by grahammechanical on 2012-10-20
[https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

Someone needs to test this. Do they not? It has to be those of us with the right hardware.

[https://github.com/Bumblebee-Project/Bumblebee/wiki/Reporting-Issues]("https://github.com/Bumblebee-Project/Bumblebee/wiki/Reporting-Issues")

Regards.

---

### Post by Vest on 2012-10-21
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
```

It seems that the repository x-swat is not available for 12.10. During the update, I got the following error:

```

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/source/Sources  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Vest on 2012-10-21
It seems that the solution from titusjaka works fine. During the installation I got the error that module nouveau is still in use. But after the reboot, I was able to see Unity 3d interface (it happend that when you upgrade Ubuntu to 12.10, all windows disappear, and I see the desktop screen only with a mouse pointer).

So, the results of the optirun command are the following:

```

$ glxspheres 
Polygons in scene: 62464
Visual ID of window: 0xa3
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile 
60.224344 frames/sec - 67.210367 Mpixels/sec
60.155543 frames/sec - 67.133586 Mpixels/sec
60.175779 frames/sec - 67.156169 Mpixels/sec
60.177334 frames/sec - 67.157905 Mpixels/sec
60.179232 frames/sec - 67.160023 Mpixels/sec
60.175836 frames/sec - 67.156233 Mpixels/sec

$ optirun glxspheres 
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCIe/SSE2
120.313576 frames/sec - 134.269951 Mpixels/sec
108.308718 frames/sec - 120.872529 Mpixels/sec
109.829023 frames/sec - 122.569190 Mpixels/sec
105.715931 frames/sec - 117.978979 Mpixels/sec
112.149951 frames/sec - 125.159346 Mpixels/sec

```

p.s. my notebook is Asus X7BS

---

### Post by titusjaka on 2012-10-22
If my solution doesn't work for someone, try to execute this commands:
```
sudo apt-get install ppa-purge
sudo apt-get purge bbswitch-dkms bumblebee-nvidia
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get upgrade ; sudo apt-get dist-upgrade
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get install bbswitch-dkms bumblebee bumblebee-nvidia
sudo reboot
```
Maybe, you just haven't the new version of linux headers.

---

### Post by Vest on 2012-10-22
I just want to add that the Ubuntu-X repository for Quantal Quetzal does not exist yet.

---

### Post by titusjaka on 2012-10-22
> **Vest said:**
> I just want to add that the Ubuntu-X repository for Quantal Quetzal does not exist yet.

Yes, that's right!
```
W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/source/Sources: 404  Not Found
W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-amd64/Packages: 404  Not Found
W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-i386/Packages: 404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Couldn't rebuild package cache

```

But anyway, this solution works :)

---

### Post by MTwebART on 2012-10-23
I don't know if it works (yet), just downloaded Kubuntu 12.10 x64, will test it in a couple of days on Krita, Inkscape, Synfig and Xara.
About the Intel driver, I've stopped using x-swat, a couple of months ago, I switched to xorg-edgers/ppa
They're a bit unstable sometimes, but the performance and power management are better.
I currently use Kubuntu 12.04 x64, kernel 3.3.7 with mesa drivers from x-org edgers and bumblebee-nvidia for optirun.

Edit:
If you want to try the alternative intel graphics driver and already have bumblebee with x-swat:

```
sudo apt-get install ppa-purge
sudo apt-get purge ppa:ubuntu-x-swat/x-updates
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install mesa-utils
sudo apt-get upgrade

```

That should work fine. Good luck! :P

---

### Post by broken plastic on 2012-11-05
> **titusjaka said:**
> Hi, guys!
You need a little effort to resolve this issue.
The answer was found here: [ click me!]("http://askubuntu.com/questions/202644/how-to-install-nvidia-optimus-driver-on-ubuntu-12-10")
You have to execute this commands:
```
sudo apt-get install ppa-purge
sudo apt-get purge bbswitch-dkms bumblebee-nvidia
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get upgrade ; sudo apt-get dist-upgrade
sudo apt-get install bumblebee bumblebee-nvidia
sudo reboot
```
That's all! My Bumblebee works now and battery doesn't run out so quickly.

I hope this answer will be helpful for you as much as for me!

yes, thank you!  worked for my asus n76vz and ubuntustudio 12.10.

for a while i was wondering if low latency kernel was an issue.  tried seemingly everything, including a fresh install on another drive

---

