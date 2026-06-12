---
title: "today's update broked my kde"
date: 2008-02-13
forum: General Help
---

### Post by dimethroxy on 2008-02-13
After today kubuntu update KDE start loading and it kick me back to KDM!

if I try to startx manually i get 3 error:

Error opening /dev/input/wacom : Success
No such file or directory.


I'm using gutsy and nvidia driver.

---

### Post by Rocket2DMn on 2008-02-13
You should be able to comment out the wacom devices in your /etc/X11/xorg.conf file unless you actually have a wacom tablet PC (a # sign at the beginning of the line does this).  Get to a TTY with CTRL+ALT+F1
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
sudo /etc/init.d/kdm start
```
If that fails, you can reconfigure Xorg, here is a guide - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by dimethroxy on 2008-02-13
I just commented those device and when i startx i get no error message but it kick me back to the console...

I've taken a look to the log of xorg and i see no error at all...

very strange ! any idea?

---

### Post by Rocket2DMn on 2008-02-13
It could be your video driver.  Did you install it with envy?

---

### Post by dimethroxy on 2008-02-13
no, from what i remember i was using the nvidia driver from the restricted module

btw, KDM start perfectly ! It just crash when i try to log into KDE..

---

### Post by dimethroxy on 2008-02-13
I just tryed to boot with an old KDE4 Beta i've installed long ago and it worked! 

seem like my video drivers are still working...  but my KDE 3.5 broked with today's update...

Argh..

---

### Post by Rocket2DMn on 2008-02-13
Well, you could reconfigure X with the tutorial i gave in my first post, perhaps just use the open source "nv" drivers to get into KDM, then get the newest drivers direct from nvidia - [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by dimethroxy on 2008-02-13
I just tryed to boot in recovery mode to try to boot KDE from the root account, and it worked perfectly ! 

Rocket2DMn, That's why i dont want to reconfigure X, cause it seem to be working... 

It seem to be only my user kde that dont work

---

### Post by Rocket2DMn on 2008-02-13
Does running the GUI from recovery use vesa?  You may not have full GUI functionality with recovery mode.  Not entirely sure though.

---

### Post by dimethroxy on 2008-02-13
Just reconfigured xorg, set it tu use VESA driver

startx:

stay at Initialise system services then kick me back to the console

(EE) Failed to initialize GLX estension (compatible NVIDIA X driver not found)

i checked my xorg.conf and it use vesa driver... I dont understand !

---

### Post by zazery on 2008-02-13
I have the same problem right now on two computers. One computer has an ATI card, and another brand which I forget.

Initially I was thinking it was due to the new kernel image presumably fixing the recent kernel exploit that was in the system updates. I'm not sure though.

---

### Post by dimethroxy on 2008-02-13
> **zazery said:**
> I have the same problem right now on two computers. One computer has an ATI card, and another brand which I forget.

Initially I was thinking it was due to the new kernel image presumably fixing the recent kernel exploit that was in the system updates. I'm not sure though.
I pretty sure there is a link between the new kernel and our problem... 

I'm tired of update broking up my system... cause it's now the first time !

---

### Post by Rocket2DMn on 2008-02-13
Let's remove the nvidia proprietary stuff - Follow the directions here to remove the conflicting software (most importantly, nvidia-glx*) - [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
You can either do that from the recovery console GUI (no internet probably), or the terminal using "sudo nano" in place of the graphics KDE text editors.
Once you enable nv or vesa you should be able to access the GUI and start fresh with the proprietary drivers.  I don't recommend using envy as it can cause problems and requires you to uninstall it + drivers before dist-upgrading.  We're still not entirely sure how well it works or if it's gonna go the way of automatix and totally screw over systems.

PS: It was probably the kernel update packages that broke the GUI, we've been seeing these a lot the last few days, but still haven't worked out a 1-method-fixes-all.

---

### Post by dimethroxy on 2008-02-13
I've removed nvidia driver, reconfigured xorg using nvidia driver, vesa or vga... 

same thing... It crash on KDE loading


this is not the first time update broke my system, and i'm damn tired of it !

I've been using kubuntu for over 2years and do not wish to reinstall everyting....

:(

---

### Post by Rocket2DMn on 2008-02-13
You can try to reinstall just the KDE stuff with
```
sudo apt-get install --reinstall kubuntu-desktop
```
You may need to check for any graphics modules that are running, too.

---

### Post by dimethroxy on 2008-02-13
i've just installed ubuntu-desktop (gnome) just for fun....

and it worked perfectly !

I will try to reinstall kde...

thanks Rocket2DMn !

---

### Post by zazery on 2008-02-14
A few hours after I posted above my dad's computer also had the same problem. He mentioned that all he did was install language packs in the update. I looked around and it turns out that there is an issue with Canadian language kde installations.

Here's the bug:
[https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/191327](https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/191327)

I uninstalled the language packages as mentioned and everything works for me now.

---

