---
title: "Tried beryl/compiz?"
date: 2006-11-22
forum: General Help
---

### Post by haxer on 2006-11-22
Hello i recently used this guide [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104) to setup my beryld i chosed this [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit) becuse i have nvidia :)
But after this step ... /usr/bin/beryl-manager as startup .. and after i restarted my computer i try to log in but my screen stops and all becomes black with little blue dotts how do i fix my problem? Anyone im really scared out now :(

---

### Post by igknighted on 2006-11-22
Are you using Dapper or Edgy?  If you have NVIDIA I would recommend you do the following:  1) Restore your xorg.conf. 2) log in to a standard session, no XGL.  3) Look up any guide to AIGLX and try to follow that (especially if you have Edgy.  XGL is unwieldy and is more like a hack on top of your xserver, while AIGLX is well integrated.  I would recommend avoiding XGL like the plague.

---

### Post by Random20230808 on 2006-11-22
There are several ways to start Xgl when you start your X session. Which one do you use?

---

### Post by haxer on 2006-11-22
I have dapper drake but how do i login .. i cant login .. all turns all black and blue :( dont this have any "failsafe" or "take away the bad things you done before" ? I need to login so i can erase the mistake i did :( I know how and where to find it but i cant login :( and the crazy thing is that i dont have any xgl installed after the installation dont know why but there isnt :(

---

### Post by Random20230808 on 2006-11-22
Don't worry and stay cool ](*,) .
When your screen is black press Alt+F1 and you'll get in terminal mode.
Before that write down from the tutorial you followed all the changes you have done to files (/etc/X11/xorg.conf etc.- this may take some time).
Then open all these files in a text editor - for example : ```
sudo gedit /etc/X11/xorg.conf
```reverse the changes and save the files.
Restart your X session (Alt+Ctrl+Backspace) and see if your X session works.

---

### Post by haxer on 2006-11-22
I have managed to get into safemod with terminal using the command firefox and opensesame :) using sudo gedit /etc/X11/xorg.conf  work but i havent done anything there so thats probably my biggest mistake :)  ... something different how to open up system preference then sessions? In command line of course :)

---

### Post by haxer on 2006-11-22
Please please please help me

---

### Post by Random20230808 on 2006-11-22
Sorry for being late. i had been offline.
I see that you have installed Ubuntu 6.06.
Do you have a problem to install (or upgrade) to 6.10?
You'll then have a pure installation to start over.
In fact a few months ago I had 6.06 and when I tried to install Xgl/Beryl did't manage to have them work correctly.

---

