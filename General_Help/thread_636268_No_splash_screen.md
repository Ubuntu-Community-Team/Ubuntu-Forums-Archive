---
title: "No splash screen"
date: 2007-12-09
forum: General Help
---

### Post by The_End on 2007-12-09
I've got no splash screen when Ubuntu loads(I had the same problem in Kubuntu), I'm using version 7.10.

Everything loads fine, except it doesn't show any splash screen, when I switch to the alt+f1 console, it shows something about Kinit trying to load a resume image that it can't find. I've tried installing another Splash Screen, and still nothing.

I've got an ATI Xpress 200 series graphics card in my laptop.

Cheers.

---

### Post by ptn107 on 2007-12-09
This is a known bug with gutsy Live CD installs.

You need to edit */etc/usplash.conf*:
```
sudo gedit /etc/usplash.conf
```
Change the values in the file to something like the following:
```
xres=1024
yres=768
```
Save the file and then in a terminal type:
```
sudo dpkg-reconfigure -phigh usplash
```
which will update the initramfs image.

---

### Post by Tompzone on 2007-12-09
Well i have the same problem, im using xubutu gusty, but when i try to use your solution the terminal states that gedit command is not found

---

### Post by santaslittlehelper on 2007-12-09
> **Tompzone said:**
> Well i have the same problem, im using xubutu gusty, but when i try to use your solution the terminal states that gedit command is not found
sudo mousepad /etc/usplash.conf

or

sudo nano -w /etc/usplash.conf

---

### Post by Tompzone on 2007-12-09
thnaks now it works

---

### Post by The_End on 2007-12-10
Awesome, it works. Thanks a bunch! :D

---

### Post by mezhaka on 2007-12-11
thanks, it works now.

---

### Post by Tompzone on 2007-12-12
Ohh hey i have to change my last word, it screwed my pc it showed the splash screen when i shutted it down but when i tried to boot up it came to a kernel panic not sincyng.
So i installed ubuntu but it has the same problem, perhaps if i use the res to 800*600 perhaps it could work?

---

### Post by pikaia on 2007-12-21
I actually have the same problem.  I used the solution and it still doesn't show the splash screen, it just shows the beige background for upwards of a minute before loading the desktop.  

I'm using Gutsy 64.  Thanks.

---

### Post by dkuhlman on 2007-12-21
> **ptn107 said:**
> This is a known bug with gutsy Live CD installs.

You need to edit */etc/usplash.conf*:
```
sudo gedit /etc/usplash.conf
```
Change the values in the file to something like the following:
```
xres=1024
yres=768
```
Save the file and then in a terminal type:
```
sudo dpkg-reconfigure -phigh usplash
```
which will update the initramfs image.

I had the same problem.  The above worked for me.  Now I can also flip to a console screen with Ctrl-Alt-F1.  Before this fix, I could not see the prompt on the console screen.

Thanks.

I'm running Gutsy x86_64 on a Toshiba Satelite laptop.

Dave

---

### Post by pikaia on 2007-12-21
First of all, thanks.  I tried your method (although I had tried it before...) and it still doesn't work.  Same situation.  Nvidia screen, beige for a minute, then desktop.  Start Up Manager didn't help either.

Any other suggestions?

---

### Post by pikaia on 2007-12-21
Okay, I'm a bit confused now.  The splash I am missing is this one:
[IMG]http://www.zenstarstudio.com/install/full/ubuntu_0007.gif[/IMG]

Will the fix you suggested restore this?  Or am I just that much of a noob?

I'm still interested in speeding my boot up if possible.  I followed the instructions from this:
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
and found it to speed it from about 3-4 minutes to about 1.5, but I'd like to get it closer to my XP boot speed which is around 20-30 seconds.

Thanks again.

---

### Post by mtcycler on 2008-04-14
Thanks I have been trying to fix my computer for some time now this was the first thing to work!! THANK YOU!!

---

