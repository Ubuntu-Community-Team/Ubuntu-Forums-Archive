---
title: "Jerky Scrolling after update to Gutsy"
date: 2007-10-19
forum: General Help
---

### Post by Poilar on 2007-10-19
After I updated from Feisty to Gutsy, suddenly all scrolling was jerky. It's most noticeable in Firefox, though I think it's there in gedit and OO too. I'm on a Thinkpad T60 with an Integrated Intel Video Card (i810 I think). Any ideas?

Thanks

---

### Post by Poilar on 2007-10-19
Found the solution. All I had to do was uninstall xserver-xgl.

I'm not entirely sure why that fixed things, but it was the solution suggested for a similar problem found here: [http://ubuntuforums.org/showthread.php?t=579762](http://ubuntuforums.org/showthread.php?t=579762)

---

### Post by cygnis1 on 2007-10-19
I also am having trouble with jerky scrolling.  so do I type apt-get remove xserver-xgl in the terminal?  Also, what happened to compiz-fusion?  I thought it was to there out of the box.  And, if if I remove it will I be able to use compiz?
Cygnis1

---

### Post by braindead_in on 2007-10-20
I was facing the same issue. Fiddled around a lot with Xorg.conf before this tip did the trick for me. Dunno  what the issues are with removing xserver-xgl but it does work.

---

### Post by cygnis1 on 2007-10-20
How do I remove it?

---

### Post by thechoyboy on 2007-10-21
I am having the same issue however I can't seem to remove xserver-xgl from the terminal - I get an error that it doesn't exist.  Also in the synaptic package manager I can't find it. I have an old sony vaio with a neomagic videocard and this is my first time trying out linux or ubuntu.

---

### Post by burningbed on 2007-10-21
sudo apt-get remove xserver-xgl

---

### Post by thechoyboy on 2007-10-21
When I do that I get the following output in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

Any ideas? Thanks!

---

### Post by silhouette on 2007-10-24
> **thechoyboy said:**
> When I do that I get the following output in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

Any ideas? Thanks!
You're probably in thinking you don't have xserver-xgl -- I had to install it after I upgraded to Gutsy, which means it wasn't automatically installed, though of course your mileage may vary. If you want to confirm you don't have it you can run ```
dpkg -l | grep xserver-xgl
``` If it's not listed, or it is listed but it doesn't have two lowercase I's at the beginning of the line, then you don't have it installed.

In that case it may be just that something else is running in the background, slowing your computer down. Opening *System -> Administration -> System Monitor* and clicking on the Processes tab will give you a better picture of the processes that are running on your computer and how much they are taxing the processor and how much memory they are taking up. (Selecting *View -> Active Processes* will limit the list to, well, processes that are currently active.)

You might just try posting the results of ```
ps aux --sort '-%cpu' | head
``` and seeing if that tells us anything.

If nothing looks suspicious, then it may be that Compiz' visual effects are still turned on (they shouldn't be, but it doesn't hurt to check). Go to *System -> Preferences -> Appearance* and switch to the Visual Effects tab. Make sure the "None" radio button is selected.

If that doesn't help, then I'm not sure.....

---

### Post by silhouette on 2007-10-24
> **cygnis1 said:**
> Also, what happened to compiz-fusion?  I thought it was to there out of the box.  And, if if I remove it will I be able to use compiz?
I found I had to install xserver-xgl before I could use Compiz -- every time I went to the Visual Effects screen and tried to change the level, an error would come back saying I couldn't do it. So, if you're not going to use Compiz, you might as well remove it.

Also, try running **dpkg -l | grep compiz | sort** to see if it's installed. This is what I get back: ```
ii  compiz                                      1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager
ii  compizconfig-settings-manager               0.5.2+git20070912-0ubuntu1            Compiz configuration settings manager
ii  compiz-core                                 1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                 0.5.2+git20070928-0ubuntu1            Collection of extra plugins from OpenCompositing for
ii  compiz-fusion-plugins-main                  0.5.2+git20070928-0ubuntu2            Collection of plugins from OpenCompositing for Compi
ii  compiz-gnome                                1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - GNOME window
ii  compiz-plugins                              1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - plugins
ii  libcompizconfig0                            0.5.2+git20070919-0ubuntu3            Settings library for plugins - OpenCompositing Proje
ii  libcompizconfig-backend-gconf               0.5.2+git20071010-0ubuntu1            Settings library for plugins - OpenCompositing Proje
ii  python-compizconfig                         0.5.2+git20070912-0ubuntu1            Compiz configuration system bindings
rc  compiz-gtk                                  1:0.3.6-1ubuntu13                     OpenGL window and compositing manager - Gtk window d
```

---

### Post by tony_gustafsson on 2007-10-25
I have the same problem. 3D effects, like turning the cube around is going really smooth... but scrolling and simple task like that is really jerky. Firefox is worst for me too.

The process Xorg seems to take 100 % CPU every 20th second or so... don't know why. I don't have xgl installed since before. This is the first time i actually made it, thanks to the new ATI drivers.

No XGL stuff installed.
Direct rendering is on
3D graphics seems to work just fine
Wtf :(

---

### Post by tony_gustafsson on 2007-10-25
Just tried glxgears... i'm up to ~5000 fps. Seems fast enough?

I tried disabling soft scrolling in firefox, but there was no difference. I thought it might be some stupid thing like that. Still needs ideas...

I saw a guide that wanted me to disable AIGLX and Composite in xorg.conf... why?! Compiz cannot work then? It also told me to disable the prop drivers before installing. Didn't see the need for that either since the fglrx version is up to date and glxgears is fast...

---

### Post by thechoyboy on 2007-10-26
In the time between my last post and this one I have switched to ubuntu. Same problem. xserver-xgl is not on this machine for sure - doesn't include any of the ubuntu gusty visual affects, but they wouldn't run on this old machine anyway (pcg-xg9).

However it still recognizes my videocard - neomagic-magicmedia256AV. I tried using the live CD for xubuntu 6.06 and noticed the same problem.

Thanks for all the tips though. I followed them all and everything seems to check out - no xserver-xgl, no processes gumming up the system. Everything runs very fast and clean, but moving windows and scrolling on any application just kills it. 

Any help of where I should go from here would be great. I'm really liking the whole ubuntu concept but it just isn't executing. Thanks!

---

### Post by thechoyboy on 2007-10-26
FIXED! All I needed to do was set my card to 16 bit instead of 24 bit using the terminal command:

sudo dpkg-reconfigure xserver-xorg

and then followed the rules and used the default settings for everything else. 

Looking through forums it seems that everyone is having similar problems but unsimilar answers.

---

### Post by pakamon on 2007-11-09
> **thechoyboy said:**
> FIXED! All I needed to do was set my card to 16 bit instead of 24 bit using the terminal command:

sudo dpkg-reconfigure xserver-xorg

and then followed the rules and used the default settings for everything else. 

Looking through forums it seems that everyone is having similar problems but unsimilar answers.

Worked for me as well \\:D/

My configuration:

Gutsy
Vostro 1700
nVidia 8600M GT
4 GB RAM
1920x1200

---

### Post by mblind on 2008-01-16
Tried the 16 bit trick.. Did not work for me.. Neither did any other the other tips in this post.

Any other ideas.. This is a real drag.

tuaw.com and espn.com are really bad..

many other sites work fine.. it's just the random site.

---

