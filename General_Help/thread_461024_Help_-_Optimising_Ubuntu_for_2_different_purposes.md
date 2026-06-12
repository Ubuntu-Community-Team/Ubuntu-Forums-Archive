---
title: "Help - Optimising Ubuntu for 2 different purposes"
date: 2007-06-01
forum: General Help
---

### Post by shavenlunatic on 2007-06-01
Hi,

I am pondering having 2 logins for ubuntu, 1 for gaming, and the other for general use.  I thougth that each user would have their own xorg.conf but it seems I was wrong as I created a new account, disabled the 2nd xorg server (dual monitors) on it, rebooted and logged in to my normal account and that also had the 2nd monitor disabled.

Basically I am looking for the best way to do this:

Be able to boot into my "gaming" profile and have:

-Lower Desktop Resolution
-Beryl disabled
-2nd monitor disabled
-gDesklets disabled
-any other system resources disabled that I can live without if I'm only gaming

and also be able to boot into my normal profile and have everything enabled

Would the best way of going about this be to have 2 seperate logins? and if so, how do I configure it to look at a seperate xorg.conf and startup apps? (i think the startup apps are seperate but i'm not at my desktop right now)

---

### Post by dave-5B on 2007-06-01
one way would be to only have one user, when you want to play a game you run a script that:
1. swaps xorg.config with xorg.config_some-name
2. restarts X11/gdm/gnome (/etc/init.d/gdm restart)
3. changes all your other settings

even with your two user way i think (though im not sure) programs like X11 will ONLY look at xorg.conf. So the way would be to have a script (or two: gaming>normal & normal>gaming) that swaps all the neccesary config files:

there will be other config files you will have to do this to but the logic is the same

---

### Post by shavenlunatic on 2007-06-02
hmm thanks, I could look into that but it's hardly ideal (last resort I hope)

any other ideas?

---

### Post by non-poster on 2007-06-02
I think you might be able to setup different runlevels, with each runlevel starting X with a specific configuration to change the monitor configuration, resolution, etc.  The separate runlevel could also have different services start/not-start at boot.  Using a different user would allow you to use a different window manager or WM configuration.

---

