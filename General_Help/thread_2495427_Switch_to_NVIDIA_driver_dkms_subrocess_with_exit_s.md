---
title: "Switch to NVIDIA driver: dkms subrocess with exit status 10 (313)"
date: 2024-02-18
forum: General Help
---

### Post by riccd on 2024-02-18
Hi, I was trying to switch to the NVIDIA driver through the "additional drivers" panel. However I get this error:
[IMG]https://www.dsrealizzazioni.it/share/Screenshot%20from%202024-02-18%2022-34-25.png[/IMG]
the error management forwards me to this link:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1573508](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1573508)
but this seems outdated to me. Any idea what to do? 
Running Ubuntu 22.04.4 LTS 64 bit on ASUS K53SV mounting NVIDIA GeForce GT 540M

---

### Post by riccd on 2024-02-18
So I apparently got this resolved. The solution is brought in this thread by @MAFoElffen
[https://ubuntuforums.org/showthread.php?t=2494273&page=2](https://ubuntuforums.org/showthread.php?t=2494273&page=2)
The Kernel update 6.5.0-18-generic seems to be incompatible with the NVIDIA 390 driver. Therefore some kind guy apparently made a patch at this repository
[https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp/+packages](https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp/+packages)
 So add the repository:
```
sudo add-apt-repository ppa:dtl131/nvidiaexp
```
purge the installed NVIDIA driver
```
sudo apt-get remove --purge '^nvidia-.*'
sudo apt-get install ubuntu-desktop
```
install the following packages(I actually did this from Synaptic package manager as I wanted to check which packages the repository had)
```
sudo apt install nvidia-dkms-390
sudo apt install nvidia-driver-390
```
reboot
I'm not too expert on linux so everything might not be perfect but it worked for me.

---

