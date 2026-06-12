---
title: "[SOLVED] How do i Set up Dual Monitors in Ubuntu?"
date: 2008-06-03
forum: General Help
---

### Post by redonwhite on 2008-06-03
Hello,  I want to set up dual monitors.  I have one monitor that is 22inch Wide Screen  1680 x 1050, and the other is 17inch 1280 x 1024.  Im running on ubuntu 8.04, compiz fusion, AWN.  Running off a Nvidia 8800, Drivers are installed and enabled.
Ive googled it and seached all over for a good secure up to date guide on doing this but cant seem to find anything =/.  I noticed some dual monitor  videos on the internet with only one cube when in Cube mode.  But since my monitors are two different sizes i thought that it would look kind of funny so maybe there is a way to get two cubes.  One on each monitor.  But not just mimicking the primary screen.  Still using it as a completey different desktop area.  If theres anything else i can tell you that would help you help me just let me know.  Thanks ahead of time for your help and time.
:)

---

### Post by Pjotr123 on 2008-06-03
Try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2)

Will work as well for setting up dual monitors.

Greetz, Pjotr.

---

### Post by redonwhite on 2008-06-03
Thank you, i love that nvidia tweaking setting thing.  its awsome =).  Now i messed with it for awhile.  But i couldnt seem to get rid of that big old cube.  Im trying to have a cube on each monitor.  So when i maximize an image it will only fill up one full screen instead of stretching it to both of them.  Any idea how i would go about tweaking that in the nvidia settings.  or if i even can?

---

### Post by Pjotr123 on 2008-06-03
Apparently, 3-dimensional visual effects aren't possible in dual monitor mode. Or so I've been told.

Well, at least you can have a 2-dimensional desktop now.  :-)

---

### Post by redonwhite on 2008-06-03
Darn i thought that was the case.  Because every video i saw with compiz running dual monitor had it just as One Big cube instead of two.  one on each monitor.  I wish i knew more about coding and stuff so i could figure out a way to set it up so we could have a cube for each monitor.  :)
By the way thank you so much for your help.  I never knew about that coold Nvidia-setting thing.  Thanks again.  Have a great day.

---

### Post by overdrank on 2008-06-03
> **redonwhite said:**
> Darn i thought that was the case.  Because every video i saw with compiz running dual monitor had it just as One Big cube instead of two.  one on each monitor.  I wish i knew more about coding and stuff so i could figure out a way to set it up so we could have a cube for each monitor.  :)
By the way thank you so much for your help.  I never knew about that coold Nvidia-setting thing.  Thanks again.  Have a great day.

Hi and I have done it with Feisty and XFCE but it was with the nvidia-settings separate x. I dont think I can do it again but I will try when I get a spare system. :)
Edit I knew I could find it 
[[IMG]http://img123.imageshack.us/img123/8429/screenshotuu2.th.png[/IMG]](http://img123.imageshack.us/my.php?image=screenshotuu2.png)

[http://ubuntuforums.org/showthread.php?t=620513&highlight=overdrank&page=5](http://ubuntuforums.org/showthread.php?t=620513&highlight=overdrank&page=5)

---

### Post by redonwhite on 2008-06-03
> **overdrank said:**
> Hi and I have done it with Feisty and XFCE but it was with the nvidia-settings separate x. I dont think I can do it again but I will try when I get a spare system. :)

yeah i tried the seperate X option.  But it left the same as twin view for some reason.  hmmmmm.

---

### Post by GammaPoint on 2008-06-03
I think you should be able to get separate cubes with two separate X servers. Last night I had my TV and monitor hooked up as the two outputs and I had the cube going on my monitor (bc I have 4 workspaces) and the TV had two sides (since I only had two workspaces on the TV I suppose).

---

### Post by redonwhite on 2008-06-03
I did get it working.  But for some reason it REALLYYYY slow stuff on my first monitor.  Not my second though wich is weird.  Like the menu drop downs and loading apps all took like 4 extra seconds then they usually did.  and the second monitor everything was working fine.  Had to reload .xorg file.

---

### Post by GammaPoint on 2008-06-03
> **redonwhite said:**
> I did get it working.  But for some reason it REALLYYYY slow stuff on my first monitor.  Not my second though wich is weird.  Like the menu drop downs and loading apps all took like 4 extra seconds then they usually did.  and the second monitor everything was working fine.  Had to reload .xorg file.

I noticed this slowdown on my first monitor as well. Anyone know a fix for it?

---

### Post by redonwhite on 2008-06-03
i Just realized how dramatic i sounded hahah "REALLLYYY slow, 4 extra seconds!" hahah.     Yeah hopefully we can find a fix for that.  I noticed when AWN wasn't on screen it quickened back up.  So it is probably an issue with AWN being on the main screen.  Just seems odd since both monitors are sucking off the same system.

Edit: I understand now.  It has two seperate X's running and Two seperate Compiz running.  So the one with AWN is bogged down.  Shame.

---

### Post by bodhi.zazen on 2008-06-03
You *should* be able to configure your monitors via :

```
gksu nvidia-settings
```, select separate monitors.

If that does not work, see if this helps :

[Dual Monitor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=240150")

---

### Post by redonwhite on 2008-06-06
> **bodhi.zazen said:**
> You *should* be able to configure your monitors via :

```
gksu nvidia-settings
```, select separate monitors.

If that does not work, see if this helps :

[Dual Monitor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=240150")

I did get the dual screens working.  Just seemed to slow down my first monitor Drastically =(.  Thanks for the help though. =)

---

### Post by _DD_ on 2008-06-07
Before I switched to my triple-monitor (which doesn't support 3d) I had a dual-monitor setup which **does** support 3D and seperate cubes are possible (although they can't be rotated independantly)..

Firstly you want to go into nvidia-settings and disable xinerama and anything like that, and use "nvidia twinview". Save these settings to x.conf and restart (just restart X if ya like by doing Ctrl+Alt+Backspace).

Next you want to download the compiz fusion settings manager...
```
sudo apt-get install compizconfig-settings-manager
```

Once that's installed, find it in your preferences menu. Assuming you already have compiz (desktop effects enabled) go into the settings for "desktop cube" and there should be a setting for what to do with multi monitor (I can't remember what the setting is called but it lets you set one big cube or one on each monitor).

I hope that's what you were looking for :)

---

### Post by Arrow000 on 2008-06-08
Hey, i tried your sulution, but when i got to the step "gksudo nvidia-settings" i got this error message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 


What does that mean and how can i fix it?

Thanks

---

### Post by chewearn on 2008-06-08
Those running separate X screens, and feeling the pain of slow menu/window opening on the first screen, this thread gave the workaround:
[http://ubuntuforums.org/showthread.php?t=536045](http://ubuntuforums.org/showthread.php?t=536045)

(workaround from page 3 onwards).

---

### Post by chewearn on 2008-06-08
> **Arrow000 said:**
> Hey, i tried your sulution, but when i got to the step "gksudo nvidia-settings" i got this error message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 


What does that mean and how can i fix it?

Thanks

Did you install nvidia restricted driver, by the GUI method, i.e. via
System > Administration > Hardware Drivers

---

