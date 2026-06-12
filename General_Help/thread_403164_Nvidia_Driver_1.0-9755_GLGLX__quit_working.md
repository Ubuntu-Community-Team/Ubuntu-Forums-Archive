---
title: "Nvidia Driver 1.0-9755 GL/GLX  quit working"
date: 2007-04-06
forum: General Help
---

### Post by airxart on 2007-04-06
-FYI-

Latest Update Manager update, dated 4/5/07, removes GL/GLX features from Nvidia Driver 1.0-9755
Two machines affected here Both have same latest ver. of ubuntu & same card (FX5200)
I do not recall what files were updated. I have not tried to reinstall the driver.
Ideas on a course of action would be appreciated.](*,)

Is there a way to get the files to change back . Uninstall update?
Is there a way to get a list of the files that where updated or a fix.

Not quite sure were to report this.
Send information on correct area to report if this is not the right area.

---

### Post by astoltz on 2007-04-06
Have a look at the file /usr/lib/xorg/modules/extensions/libglx.so - it should be a symbolic link to the Nvidia version of that file: libglx.so.1.0.9755

The latest xorg update overwrote that sym-link with the xorg version - just change it back and you should be OK.

---

### Post by airxart on 2007-04-07
> **astoltz said:**
> Have a look at the file /usr/lib/xorg/modules/extensions/libglx.so - it should be a symbolic link to the Nvidia version of that file: libglx.so.1.0.9755

The latest xorg update overwrote that sym-link with the xorg version - just change it back and you should be OK.

:KS 

Thanks I'll try looking there.

---

### Post by airxart on 2007-04-07
Where would I find or how do I create the symbolic link. :roll:

---

### Post by Nachimir on 2007-04-07
It's easy with the GUI, though in my case the file was located a directory higher: /usr/lib/xorg/modules/

Simply rename the existing symlink to something like libglx.so.backup, then go into /usr/lib/xorg/modules/extensions, right click on libglx.so.1.0.9755 (or whatever your latest version is), and click "Make link". Rename the fresh symlink to libglx.so, then cut and paste it up a directory into /usr/lib/xorg/modules/

Should work after reboot, you can make sure by typing glxgears into the console; if you get 3D gears then you know all is well. Also, worth looking in /var/log/Xorg.0.log and posting it here if you still have problems. At present, it will probably contain some lines about failing to load GLX; this is due to the symlink not pointing to the right nvidia driver.

---

### Post by astoltz on 2007-04-07
From the command line it's: ```
cd /usr/lib/xorg/modules/extensions/
sudo mv libglx.so libglx.so.backup
sudo ln -s libglx.so.1.0.9755 libglx.so
```
And if your original libglx is up one directory like twoflush, then add one last command```
sudo mv libglx.so ..
```
Then either a reboot or just re-start X with ctrl-alt-backspace

---

### Post by airxart on 2007-04-07
Thanks . I will try both fixes.
Gui on one computer& terminal on the other computer.
:)

---

### Post by raffytaffy on 2007-04-07
you can also try this method. 
Edit your xorg.conf and replace "nvidia" with "nv"  - reboot computer. on login screen go into console login, reinstall nvidia driver. and let it reconfigure your xorg. and should fix the problem. note- this is using the nvidia installer from their website

---

### Post by airxart on 2007-04-07
I used the terminal fix Astolz suggested.
Twoflush, I did not know how to log in to get sudo/root type access to 
rename using the GUI interface.
Raffytaffy I'll keep your information just in case I want to go that route in
the future.
I did a shut down  restart, (restart only doesn't work) and all was well
with both machines. :) 

Thanks for all the help.
Some day I hope I can help too.:D

---

### Post by Nachimir on 2007-04-07
> **airxart said:**
> Twoflush, I did not know how to log in to get sudo/root type access to 
rename using the GUI interface.

Ah, of course.

If you right click, make a launcher with whatever name and icon you like and set the command to "gksu nautilus", it will ask for your password every time you launch it and allow you to make system changes through that window.

I've become so used to it that I forgot it isn't standard ;)

---

### Post by airxart on 2007-04-08
> **twoflush said:**
> Ah, of course.

If you right click, make a launcher with whatever name and icon you like and set the command to "gksu nautilus", it will ask for your password every time you launch it and allow you to make system changes through that window.

I've become so used to it that I forgot it isn't standard ;)

Thanks again8-)

---

### Post by carlosK on 2007-04-08
Thank you for this thread.  I was pulling my hair out as to why my system suddenly started quitting X any time I enabled Compiz.  Now everything is working fine.

Should this be filed as a bug? Is this a bug?

---

### Post by oimon on 2007-04-10
may i also add thanks for this thread. hopefully others will find it too, this update spoilt my evening.
this thread redeemed it. 
if anyone else is searching for "beryl crashing X" then maybe this thread will pop up :)

---

### Post by king_arthur on 2008-03-30
> **astoltz said:**
> Have a look at the file /usr/lib/xorg/modules/extensions/libglx.so - it should be a symbolic link to the Nvidia version of that file: libglx.so.1.0.9755

The latest xorg update overwrote that sym-link with the xorg version - just change it back and you should be OK.
I would like to try this fix as running Google Earth (i.e. OpenGL) crashes my xserver savagely.

Where is the nvidia version of that file located?

Can't find it in the kernel modules section on Hardy.. :(

---

### Post by toasterboy1 on 2008-06-14
Thanks astoltz. Solved my crack-attack crash problem.

---

