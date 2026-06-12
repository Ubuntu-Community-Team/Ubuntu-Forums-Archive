---
title: "XGL and compiz annoyances"
date: 2006-07-24
forum: General Help
---

### Post by javierfh on 2006-07-24
Hello, I have installed the XGL/compiz following the link here [http://www.ubuntuforums.org/showthread.php?t=131267&highlight=inkscape+xgl](http://www.ubuntuforums.org/showthread.php?t=131267&highlight=inkscape+xgl).
Everything was just fine, I love it and works very nice.
But when using it for a while, I have noticed few things and would like to know if anyone has encountered them too and if any of you knows how to fix them.

-Nvidia settings, (or whatever is the name, I cant remember and im not at home right now) has lost all the tabs, there is only one page with few boxes you can tick but not more than 5, all the other tabs, color adjustments and so on, are gone.
-VLC, looses the upper part and I cant move it around, unless I use right click in the app bar and right click move.
-Inskape, when selecting some shape and right click on fill and stroke (for example), the popup window opens and everything seems to work there, but there is no way to close it nor move it somewhere else. There is no close option.
-F-spot, when clicking full screen makes a picture that it goes to the corner of the screen and its not bigger than 3 cm long 
-Every now and then, I get some message like gnome has crashed and I loose the upper part of all the windows. The only way to get it back it is to run again "thefuture" script, used to start the XGL/compiz
 

So any idea? I have read a lot about these quinn repositories and the fancy xgl things there, but I was just concerned that if I install these, then updates would be more difficult. Is that so? 
Do you know what happens if I re-install again the nvidia settings? will that mess the xgl/compiz I have now?

I hope this makes some sense and if you think I wasn't clear enough please feel free to ask more, Im quite new in linux and all the possible help would be more than welcomed.

Thanks in advance,

Javi

---

### Post by kopinux on 2006-07-24
i also have some brightness problem because nvidia-settings functionality is gone.

---

### Post by javierfh on 2006-07-24
Hi,

So what happens if you re-install nvidia settings thingy,will that screw the XGL settings? will it work anymore?
Im little bit concerned about that and didnt want to mess there, hopping that some new update will fix that.
Im also considering these quinn scripts and work, seems there is ativity there, but im afraid to not been able to get updates later on.

Anyone else found this same problem? any ideas? solutions?

---

### Post by mcduck on 2006-07-24
Those problems are pretty much all just bugs in the old version of Compiz that's available in Ubuntu's repositories. Updating to QuinnStorm's version would probably fix them all ;)

And no, it doesn't make updates any harder. QuinnSorm's packages are updated with the update manager just like everything that you install with apt-get/Synaptic.

---

### Post by javierfh on 2006-07-24
So i guess ill give them a try :)

Is it possible to install them on top of what i have installed?
or do you have to un-install something there?or just follow the tutorial how to install these Quinn packages?

Thanks again,

Javi

---

### Post by mcduck on 2006-07-24
If you add the repositories in your sources.lst and upgrade that should do most of the job.. Altough there are some changes you might need to do, and some extra packages that you'll want to install (for example 'gnome-window-decorator' is now known as 'cgwd' so you need to make sure it's installed and fix your compiz start scripts to use that command instead..

You could of course make sure that the upgrade goes fine by checking some howto's in Compiz forums: [http://www.compiz.net]("http://www.compiz.net")

---

### Post by 3rdalbum on 2006-07-24
When I try to use a panel launcher in Gnome with XGL, I get full digital noise across the whole screen (probably because of the black bars that Gnome draws when you use a launcher).

I also have problems when logging out from Gnome, and logging out on KDE seems to kill X. I can't run multiple DEs now :-(  It's almost perfect on XFCE, except that saving a session when Compiz is active means that the next time you start XFCE, you don't have window decorators; and occasionally XFCE crashes after only a few seconds.

That's currently the price I pay for an awesome-looking system! (I find myself using XFCE/Compiz now)

---

### Post by mcduck on 2006-07-25
> **3rdalbum said:**
> When I try to use a panel launcher in Gnome with XGL, I get full digital noise across the whole screen (probably because of the black bars that Gnome draws when you use a launcher).

You can get rid of most of those black wireframe animations if you open gconf-editor and disable 'apps/panel/global/enable-animations'-key..

---

