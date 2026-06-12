---
title: "Just installed Nvidia drivers"
date: 2006-12-20
forum: General Help
---

### Post by papa6 on 2006-12-20
I just installed my nvidia drivers for my older but useful Nvidia Geforce 6200 SE. not a great card but i feel that linux supports Nvidia better or vice versa. can anyone tell me how to get my monitor setup? there doesn't seem to be a utility to do this in my edgy eft distro.

thanks

---

### Post by padre999 on 2006-12-20
What do you mean by getting your monitor setup? Is it not working? What do you want to change, fix?

---

### Post by papa6 on 2006-12-20
Yes precisely. most distros have a monitor setup utility. there i can setup make, model and vert refresh and refresh rates for my monitor

---

### Post by padre999 on 2006-12-20
Go to Start>System Settings or press ALT+F2 and enter "systemsettings". There you will find a module for monitor&display with which you can adjust resolution etc.

+++++sorry. I assumed you are running KDE++++++ Not sure how it works in GNOME!? Someone? But should be similar anyway.

If you need some more serious setup because you have problems with the monitor you can do it the tough way as described in [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) but this can also mess up your system, so handle with care.

---

### Post by anjin on 2006-12-20
> **papa6 said:**
> Yes precisely. most distros have a monitor setup utility. there i can setup make, model and vert refresh and refresh rates for my monitor

You can also try this:

1) open a terminal/shell window
2) type: sudo dpkg-reconfigure xserver-xorg
(or, if you're using another xserver, substitute that)

That'll run you through a whole bunch of X11 setup questions, four of which are the make, model, horizontal, and vertical refresh rates for your monitor.


Good Luck!
8)

---

### Post by padre999 on 2006-12-21
> **anjin said:**
> You can also try this:

1) open a terminal/shell window
2) type: sudo dpkg-reconfigure xserver-xorg


I mentioned that in the post above. If you follow the link you'll see. 

But maybe you could tell us how to start the normal monitor&display setup window in Gnome where you can change resolution etc. I see you are a Ubuntu user... I don't know how to do it (again see above) as I am a Kubuntu user.

Or someone else please... Come on guys. Can't be so difficult. Drop a line.

thanks

---

### Post by bonzodog on 2006-12-21
There isn't monitor set-up gui for gnome as such, but there is a resolution setup facility, although this doesn't alter the system wide settings - just the settings for that user account. 

I'm afraid that the main way of setting resolutions for monitors for Linux still lies in editing the /etc/xorg.conf file. I know that there is a project in place for gnome to do a GUI X setup, but it's still in development. You see, X is a very complicated piece of kit, and highly advanced. 
To add to this, they have, with the most recent release of X, changed the way it's configured. 
It used to be a monolithic piece of kit, but now its modular.

Anyway, it depends what you want to do with the monitor set-up wise - the resolution? if thats the case, then just add the new res to the top line of the res settings area of /etc/xorg.conf. If you take sometime to just read this file you will see that it's divided up into areas, and each area sets up a different thing. One area, near the bottom contains the bit depths and resolutions, listed highest to lowest. Incidentally, when I installed the drivers for my Nvidia 6200, my monitor was already running at it's best resolution - 1280 x 1024, and my xorg.conf file reflected this.

---

### Post by padre999 on 2006-12-21
> **bonzodog said:**
> there is a resolution setup facility, although this doesn't alter the system wide settings - just the settings for that user account. 
I think that's what we are looking for at the moment. How do you switch resolution, refresh rate on the fly in GNOME? There must be a possibility to choose from the resolutions specified in the Xorg.conf...

---

