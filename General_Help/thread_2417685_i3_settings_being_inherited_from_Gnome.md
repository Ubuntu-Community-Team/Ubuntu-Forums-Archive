---
title: "i3 settings being inherited from Gnome"
date: 2019-04-25
forum: General Help
---

### Post by frrobert on 2019-04-25
I am using i3 window manager on Ubuntu 16.04.  I noticed a few of the settings I try to change in i3 can only be changed in a Gnome Session.

For example, I tried to use feh or nitrogen to set up wallpaper in i3 with no luck.  The wallpaper is inherited from Gnome.  If I logout of i3, login to Gnome and change the wallpaper, and then login to i3 the wallpaper is changed.

I just know enough to be dangerous.  I am guessing some X11 session file is being called that uses Gnome settings even though I never login to Gnome.

I am using LightDM.

Thanks,

---

### Post by #&amp;thj^% on 2019-04-25
Sorry this will be just one of those quick and dirty, but if you don't get a satisfactory solution for your case,
If you use "pcmanfm" as a file manager, it can handle a desktop background wallpaper with "pcmanfm --desktop" command.

Also this may help: [https://askubuntu.com/questions/407514/nitrogen-is-not-setting-the-wallpaper-when-i-start-i3](https://askubuntu.com/questions/407514/nitrogen-is-not-setting-the-wallpaper-when-i-start-i3)

---

### Post by frrobert on 2019-04-26
1fallen,

Thanks for the pcmanfm -desktop idea. That works.  feh, xsetroot, or nitrogen will not.  

I have found the issue.  It is not what I thought.

For some reason I3 config will not execute any terminal based programs, if the program is graphical in nature it can be run from I3 config.

---

### Post by frrobert on 2019-04-26
I found out the fix.  I am not sure why  it works but it works.  For some reason my terminal based programs will only run with exec_always in the config file even on a fresh boot.

---

### Post by #&amp;thj^% on 2019-04-26
Thanks for the share, and keep up the good fight.:)

---

