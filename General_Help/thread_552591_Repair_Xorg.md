---
title: "Repair Xorg"
date: 2007-09-16
forum: General Help
---

### Post by strange_cathect on 2007-09-16
I was attempting to set up a dual monitor and royally messed up my xorg.conf file.

I have followed the advice here in the forums to use **sudo dpkg-reconfigure xserver-xorg** to get a fresh file but whatever I do I am unable to restart X.  I just get errors about "no screens found."

I'm at the end of my rope because I'm a professor and have a ton of papers to grade (which are all on my desktop).  

Can anyone give me some help about how to get this fixed?  I would really appreciate it.

---

### Post by yabbadabbadont on 2007-09-16
Try adding the **-p high** option to your dpkg-reconfigure command.

```
sudo dpkg-reconfigure -p high xserver-xorg
```

---

### Post by strange_cathect on 2007-09-16
Hi,

I tried your command, which brought up the same series of configuration questions.  But after about two questions the "wizard" ended.  After, I tried to issue "startx" but again there were "no screens found."  Ideas?  Thanks for your help, by the way.

---

### Post by yabbadabbadont on 2007-09-16
Create a new post and please attach both your /etc/X11/xorg.conf and /var/log/Xorg.0.log files.

---

### Post by strange_cathect on 2007-09-16
Hi,

All I have is a command prompt at my desktop.  I'm typing to you on another laptop.  I don't know if I can get the other files to you.  Even when I try to restart and use the safe mode I can't get GUI.

---

### Post by yabbadabbadont on 2007-09-16
In that case, try renaming the /etc/X11/xorg.conf file to something else, like xorg.conf.borked, and then run the dpkg-reconfigure command again.  You might even try running ```
X -configure
``` and then see if the xorg.conf that it generates will work.

---

### Post by strange_cathect on 2007-09-16
Hi,

No dice on the X -configure command.  I got an "X" for the cursor and a white-and-black checked screen with nothing in it.

Sorry, I don't know how to rename the .conf file from the prompt.

---

### Post by yabbadabbadont on 2007-09-16
The "X" cursor and checked screen means that X actually ran though...

To rename a file/directory from the command line use:
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.borked
```

---

### Post by strange_cathect on 2007-09-16
Ok, I renamed the file then tried to create the new xorg.conf file as you suggested.  After going through the questions I tried start X but again got a "Fatal Server Error": No Screen Found.  

I'm stumped.

---

### Post by w4ett on 2007-09-16
When you :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

select "vesa' as the driver and then save and

```
startx
```

This SHOULD give you a basic video driver and get you back into your desktop.

---

### Post by strange_cathect on 2007-09-16
Ok, thanks, that is better...

I was able to get to the login screen, however when I logged in, my screen when completely white with no desktop items.  Just the cursor and the white background. I suppose this might be due to the fact that I had the 3-D desktop enabled?  I have an NVIDIA card which is also a pain to configure too.

I am able to use the GUI in recovery mode.

Any other ideas?

---

### Post by Kieffer87 on 2007-09-16
> **strange_cathect said:**
> Ok, thanks, that is better...

I was able to get to the login screen, however when I logged in, my screen when completely white with no desktop items.  Just the cursor and the white background. I suppose this might be due to the fact that I had the 3-D desktop enabled?  I have an NVIDIA card which is also a pain to configure too.

I am able to use the GUI in recovery mode.

Any other ideas?

I see the login screen just fine, but once I login the screen is just all white. I'm on a Dell 600m. It used to work fine then I messed with the conf file and broke it haha.

---

### Post by Kieffer87 on 2007-09-16
Ok I just messed around a bit and loaded in recovery console, started x. It all was fine until I switched the desktop effects on again. Is there anyway to turn them off at the console?

---

### Post by Kieffer87 on 2007-09-16
Turns out I had selected the wrong video driver. The Vesa didn't work so I switched to ATI and it loaded right up. Might want to experiment with the different drivers available.

---

