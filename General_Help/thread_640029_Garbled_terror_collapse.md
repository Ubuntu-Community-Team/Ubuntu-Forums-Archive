---
title: "Garbled terror collapse"
date: 2007-12-13
forum: General Help
---

### Post by silverguy on 2007-12-13
hi there,

long time windows user here trying to make the gap that much bit smaller, progressing from xp to ubuntu.

I have had varying degrees of success, but i seem to have hit hard times.

I have decided to hit Linux with my very own brand of "trial and error" making small leaps every so often. How ever i manged to change my resolution to something obscene and now ubuntu displays like a kaleidoscope on acid, in many small Little fractious elements. (the course has 4 bits of its self splayed across the desktop... i have no idea whats going on...) 

I did change my drivers to propriety drivers instead of the open source one. I was using Envy and Nvidia to control my display , at 1280 * 720, and every thing was fine. But i wanted to try more trial and error and in the middle of trying to get WINE to work, now why did i change the display... something to do with photo shop.

Any oh i used sudo apt-get install nvidia-glx-new  in the vain hope it would save me again. but no joy. I uninstalled the nvidia driver program (which worked prior) and i got an error while trying to initialise "the restricted driver".

Something like "Linux-restricted-module-20.14.4-server" not installed restricted driver will not run...

any ho, i am going back into Linux now to try and edit the xorg.conf through sudo nano /etc/x11/xorg.conf.... and see if i can change the resolution that way..


anyways having a great time trying to get Linux to work, wow a legal OS on my PC who would have thought it.!

Anyways i hope you can give me pointers or some kind of advice would be greatly appreciated

Ian

:KS

---

### Post by silverguy on 2007-12-24
noone?

:(

---

### Post by quoderat on 2007-12-24
If I understand the problem correctly, it sounds as if you have the resolution set incorrectly.

If X is attempting to run with this incorrect res, just do CTRL-ALT-BACKSPACE, and drop to a terminal. (Log in, if necessary.)

Then, do sudo nano /etc/X11/xorg.conf

Under section "Screen" (I believe), should be some lines about what resolution your monitor is set. Change these lines to match your monitor's correct resolution.

Mine is configured in Twinview, so not sure if posting mine would help you -- but if you cannot get it to work, feel free to post your xorg.conf file, so we can troubleshoot it.

---

### Post by Craigus on 2007-12-24
Just boot into recovery mode, or do ctrl-alt-F1 to get a text terminal, and do:> sudo dpkg-reconfigure -phigh xserver-xorg

That will set xorg.conf to sane defaults.

---

### Post by silverguy on 2007-12-25
Thanks for your reply!

yeh i have been using 

sudo dpkg-reconfigure -phigh xserver-xorg 

sudo nano etc/X11/xorg.conf as well mainly

startx just failed me even though i had minimal res set (800*600 and 640*480)

i changed my mice input with dpkg-reconfigure but reinstalling the xorg 

sudo rm -r /etc/X11
sudo apt-get install --reinstall xserver-org 


got me further than i had in hours and i managed to log into a gui although it was limited to a terminal .

After fiddling a bit more i chanced upon altering the middle left monitor icon (at the login screen of ubuntu) to start the gnome normally once again.

Can anyone explain the insanely small font used by Ubuntu at the start login screen of ubutnu or how to change the system font?

anyway i hope this post helps out anyone with similar issues

with

No screen 

fatal server error XIO 104!

:)

---

