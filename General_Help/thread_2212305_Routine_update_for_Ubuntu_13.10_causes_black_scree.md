---
title: "Routine update for Ubuntu 13.10 causes black screen with x-shaped cursor"
date: 2014-03-20
forum: General Help
---

### Post by benryansflyingcircus on 2014-03-20
Hi,

I've been using Ubuntu 13.10 for a while now (with cuda 5.5 installed according to this answer [http://askubuntu.com/questions/380609/anyone-has-successfully-installed-cuda-5-5-on-ubuntu-13-10-64-bit](http://askubuntu.com/questions/380609/anyone-has-successfully-installed-cuda-5-5-on-ubuntu-13-10-64-bit)) and everything has been working fine. Last night I installed some updates the software manager requested and switched off the computer. This morning I came in and booted up the computer. I proceed through the OS loading screen with the 'ubuntu' logo and the little dots that represent loading normally, but after that the screen goes black and I just have an x-shaped cursor. I've tried a variety of tricks through the TTY console but nothing has worked, and I'm stuck without a GUI. Has anyone seen this problem before, and is there a known solution? I've tried:

- Backing up my xorg.conf file

- Reinstalling the ubuntu desktop:

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

- Purging nvidia* and reinstalling the latest NVIDIA drivers (note that I compiled these with GCC 4.6 instead of GCC 4.8, as required previously by the CUDA installation). 

Any help would be greatly appreciated!

---

### Post by cody1233 on 2014-03-20
HAve you tried booting into recovery mode and using dpkg-reconfigure xserver-xorg?  I think just reinstalling it keeps the configuration options unless --purge is used.  Worth a shot :D

---

