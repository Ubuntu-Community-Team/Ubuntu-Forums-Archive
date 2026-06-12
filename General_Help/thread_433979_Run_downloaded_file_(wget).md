---
title: "Run downloaded file (wget)"
date: 2007-05-05
forum: General Help
---

### Post by Matthaeus on 2007-05-05
I am having lots of trouble getting xserver to run using nvidia drivers - i think i have found a fix

> I have solved the problem and built nvidia-glx with pbuilder.
Can anyone try it and tell me if it solves the problem, please?
here are the instructions:
1) download this file by typing:
wget h**p://albertomilone.com/ubuntu/nvidia/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
2) type:
sudo apt-get --purge remove nvidia-glx-new
3) install the package you downloaded (only for Feisty 32 bit, sorry)
4) log out and press CTRL+ALT+Backspace
5) post your /var/log/Xorg.0.log

But  how does one complete step 3? what command has to be typed to run the file?
This is my first day of linux, so be nice - i realise it must be something extremely simple as searching hasn't turned anything up.

I tried downloading the file to desktop (with firefox) and running it from there, but it gives me a conflict error - package isn't compatible with nvidia-glx  (although i have ran step 2 as well as sudo aptitude remove --purge nvidia-*).

Many thanks in advance, Matt.

-----------------------------------------

Worked it out.  sudo dpkg -i  file.deb

---

### Post by Thingymebob on 2007-05-05
sudo dpkg --install nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
(that 2x - before the install)
the password you're asked for is the one you used for the initial user when you set up ubuntu (most likely your login password)

---

