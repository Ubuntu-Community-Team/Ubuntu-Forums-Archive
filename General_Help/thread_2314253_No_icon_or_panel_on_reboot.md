---
title: "No icon or panel on reboot"
date: 2016-02-19
forum: General Help
---

### Post by SUPERFITTER on 2016-02-19
I am running Ubuntu 14.04 with Cinnamon.  I just updated and upgraded the system. On reboot I only have a light colored desktop with no icons or panel.  I can right click and change the desk top to the ones in Ubuntu only. I can get a terminal with Ctrl+ Alt + T.  Cinnamon seems to be the problem.  Is there a way to logout of Cinnamon and log into Ubuntu with the terminal?  Is the another way to correct this problem?
Thank You

---

### Post by grahammechanical on 2016-02-19
When you installed Cinnamon did you remove Unity? If you did not then you should be able to select a Unity session from the login screen. 

Regards

---

### Post by QDR06VV9 on 2016-02-19
Have you used this command yet

***For cinnamon do:***
```
gsettings reset-recursively org.cinnamon   
```

that should reset the complete panel to cinnamon  defaults..
And as far as invoking Unity from the terminal see this: [http://askubuntu.com/questions/38579/how-do-i-restart-a-unity-session-from-the-terminal](http://askubuntu.com/questions/38579/how-do-i-restart-a-unity-session-from-the-terminal) 
Regards

---

### Post by SUPERFITTER on 2016-02-19
> **grahammechanical said:**
> When you installed Cinnamon did you remove Unity? If you did not then you should be able to select a Unity session from the login screen. 

Regards

I cannot get a login screen, just a picture on the desktop with no icons or panel. This machine has a dual boot with Win 7 and has a grub menu that still allows me to pick operating systems. Before I could logout and then log into Ubuntu 14.04 with Unity.

---

### Post by SUPERFITTER on 2016-02-19
> **runrickus said:**
> Have you used this command yet

***For cinnamon do:***
```
gsettings reset-recursively org.cinnamon   
```

that should reset the complete panel to cinnamon  defaults..
And as far as invoking Unity from the terminal see this: [http://askubuntu.com/questions/38579/how-do-i-restart-a-unity-session-from-the-terminal](http://askubuntu.com/questions/38579/how-do-i-restart-a-unity-session-from-the-terminal) 
Regards

I tried this no change, still just have a picture.

---

### Post by QDR06VV9 on 2016-02-19
Ah she's a stubborn one then.
ctrl + alt + t  Then run it with this:
```
DISPLAY=:0 ccsm
```

Everything should spring into life but if it doesn't, you might have to restart. 
You can do that by going back to the terminal and running "sudo reboot".

A good  solution for me (has solved the same problem):

in a terminal:

```
export DISPLAY=:0   
sudo dconf reset -f /org/compiz/

```
and then

```
setsid unity

```
I hope this helps.

---

### Post by SUPERFITTER on 2016-02-19
> **runrickus said:**
> Ah she's a stubborn one then.
ctrl + alt + t  Then run it with this:
```
DISPLAY=:0 ccsm
```

Everything should spring into life but if it doesn't, you might have to restart. 
You can do that by going back to the terminal and running "sudo reboot".

A good  solution for me (has solved the same problem):

in a terminal:

```
export DISPLAY=:0   
sudo dconf reset -f /org/compiz/

```
and then

```
setsid unity

```
I hope this helps.

Thank You runrickus

I had to run everything to get login back. Now I can login again. I have a question about running compiz.  Ubuntu says to run at your own risk when I installed the program. What is the risk of running the program?

---

### Post by QDR06VV9 on 2016-02-19
Unity uses compiz! That warning is just standard when launching compiz setting manager, you can disable that warning if you choose.
That's kind of a loaded question, Just depends on your computer specs IE: CPU +Memory+ Video card or GPU 
System Memory  is the lesser needed of requirements (4Gigs is Good) CPU most 64 bit cpu's are satisfactory, Video Cards or GPU's is where you need a little hoarse power..(with it's own ram or memory) 
But Compiz is a compositing window manager for the X Window System, using 3D graphics hardware to create fast compositing desktop effects for window management. Effects, such as a minimization animation or a cube workspace, are implemented as loadable plugins. Because it conforms to the ICCCM standard, Compiz can be used as a substitute for the default Mutter or Metacity, when using GNOME Panel, or KWin in KDE Plasma Workspaces. Internally Compiz uses the OpenGL library as the interface to the graphics hardware.
I would just be careful of having too many options or animations going on..
Kind Regards

---

