---
title: "I think I broke the GUI."
date: 2013-02-07
forum: General Help
---

### Post by AgitatedOregano on 2013-02-07
Like, in my infinite wisdom I killed lightdm.  'cause I needed to do  that to install some stuff that would get Blender Cycles running.  And  now my computer looks like [this]("http://i284.photobucket.com/albums/ll30/izetehubermuffin/screen.png"):

[http://i284.photobucket.com/albums/ll30/izetehubermuffin/screen.png](http://i284.photobucket.com/albums/ll30/izetehubermuffin/screen.png)

Workspaces  are unusable.  Three-finger trackpad window dragging is broken.  Compiz  often momentarily crashes when I try to undock a window.  And the side  menu and the top bar with the clock and everything are both gone.

I did try reinstalling lightdm from command line.  But that's about it.  Any suggestions would be super welcome.

---

### Post by papibe on 2013-02-07
Hi AgitatedOregano.

Killing lightdm has the effect of killing your desktop session, and all GUI programs.

It is a temporary situation as if you restart your computer it should be OK again:
```
sudo reboot
```
There's a chance that you can get to a text-mode console by pressing Ctrl+Alt+F1

If you can login there, you can restart your session by running:
```
sudo service lightdm start
```
That should take you to the GUI. If not, press Ctrl+Alt+F7

Hope it helps. Let us know how it goes.
Regards.

---

### Post by AgitatedOregano on 2013-02-08
Your suggestions are heartily appeciated!  However, I've already tried restarting my computer, and restarting lightdm from the command line : (.  It still looks like this.

---

### Post by fdrake on 2013-02-08
how about re-installing it? 
```

sudo apt-get install re-install lightdm

```

---

### Post by GnuKian on 2013-02-08
```
sudo dpkg-reconfigure lightdm
```

---

### Post by AgitatedOregano on 2013-02-08
Thanks!  However, I have tried apt-get remove followed apt-get install before.  The re-install command didn't seem to work--computer couldn't find the command, I mean.  Reconfigure seemed to execute properly but didn't change anything :  (

---

### Post by GnuKian on 2013-02-08
>  The re-install command didn't seem to work```
sudo apt-get install --reinstall lightdm
```Check after "Reboot".

---

### Post by deadflowr on 2013-02-08
If reinstalling lightdm is becoming too problematic for you, try installing gdm.

Then use the reconfigure method described earlier and set it to gdm and restart the service as also previously posted, but as gdm instead of lightdm.

---

### Post by Zteam on 2013-02-08
Try to log in using the guest-account if that works, the damage is only in your user-profile, wich means you can just create a new user and move your files over there. :popcorn:

---

### Post by AgitatedOregano on 2013-02-08
You are all awesome.  Thanks a bunch!

Unfortunately, the problem remains.  Reinstall didn't work, and the new user account (as well as the guest account) both have the same problem.  I did install and switch to gdm, and while the login screen--which, by the way, has appeared fully functional this entire time--changed, logging in produces the usual menuless, weird-windowed screen.

To be more specific about the start of my troubles, a couple days ago I executed this command:

```
sudo service lightdm stop
```

while logged in and not in commandline mode, and had to hard restart because, if I remember correctly, only the shell was left and I couldn't figure out interact with my computer.  The problem really started when I logged back in, but stopping lightdm must've done something to the settings I guess?

Anyway, thanks again for all your help so far.

---

### Post by deadflowr on 2013-02-08
Looking over your screenshots, it would seem killing lightdm is probably not the problem. Though it most likely caused the problem.
The problem looks more like Unity isn't loading correctly.
Try:
```
unity --reset
```

And see if that helps.

Or install compizconfig-setting-manager and enable it through the Ubuntu unity section.

Then again I'm just spit balling at possible solutions.

---

### Post by JKyleOKC on 2013-02-08
> **AgitatedOregano said:**
> To be more specific about the start of my troubles, a couple days ago I executed this command:

```
sudo service lightdm stop
```

while logged in and not in commandline mode, and [COLOR="Red"]had to hard restart[/COLOR] because, if I remember correctly, only the shell was left and I couldn't figure out interact with my computer.  The problem really started when I logged back in, but stopping lightdm must've done something to the settings I guess?That hard restart is probably what caused your problem, by corrupting one or more system files. Unfortunately, determining just which they are is not easy. The simplest solution may be to use a Live CD/USB to access your home directory, copy all your important files to an external drive or flash drive(s), and re-install the system.

---

