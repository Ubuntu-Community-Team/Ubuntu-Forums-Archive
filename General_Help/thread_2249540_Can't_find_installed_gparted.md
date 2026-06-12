---
title: "Can't find installed gparted"
date: 2014-10-22
forum: General Help
---

### Post by bik-npl77 on 2014-10-22
Hello,
 
GParted is installed in my system. It says installed in application center and if I try to install from console it says "GParted is already the newest version" but I cannot open it from either places. How do I open GParted? Also, my usr/bin only has "flash-player-properties", there are no hidden files too same is the case with usr/share/applications although I have installed multiple application. So what's going on here?

---

### Post by fantab on 2014-10-22
Try in terminal:
```
sudo gparted
```

Tell us what the terminal says...

---

### Post by CantankRus on 2014-10-22
What happens when you run in terminal....
```
gparted-pkexec
```

---

### Post by bik-npl77 on 2014-10-22
Thanks for the reply guys! All right so here it is....I really can't figure it out...it says it's installed then again it asks to install!!

---

### Post by fantab on 2014-10-22
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Post back if you see any errors.

EDIT: Are you on Ubuntu-unity or Ubuntu-gnome? If you are on Ubuntu-gnome then 'compiz' won't work AFAIK.

---

### Post by bik-npl77 on 2014-10-23
No, it doesn't show any errors, it's just running the upgrade...
Yeah it's Unity, I don't know why it says GNOME...perhaps sth wrong with archey! It doesn't matter I guess...

---

### Post by CantankRus on 2014-10-23
> **fantab said:**
> 
EDIT: Are you on Ubuntu-unity or Ubuntu-gnome? If you are on Ubuntu-gnome then 'compiz' won't work AFAIK.

Unity is a graphical shell for the **GNOME** desktop environment.
GNOME Shell is the default graphical shell of the GNOME desktop environment.
So whatever shell you use, **GNOME** is going to show as the desktop environment.

---

### Post by fantab on 2014-10-23
> **bik-npl77 said:**
> No, it doesn't show any errors, it's just running the upgrade...
Yeah it's Unity, I don't know why it says GNOME...perhaps sth wrong with archey! It doesn't matter I guess...

After it upgrades try opening gparted again and if it does not work, then the easiest way out will be to re-install ubuntu. Especially since:
> Also, my usr/bin only has "flash-player-properties", there are no  hidden files too same is the case with usr/share/applications although I  have installed multiple application. So what's going on here?

---

### Post by vasa1 on 2014-10-23
I found "my usr/bin only has "flash-player-properties", there are no hidden files too same is the case with usr/share/applications although I have installed multiple application" odd as well.

What about **/usr/bin**? Could we see a little of that?

What do you see when you run exactly **ls /usr/bin | more**?

---

### Post by bik-npl77 on 2014-10-23
okay guys, so I guess I helped myself...I uninstalled gparted and installed it again from the software center and look what happened: (in the screenshot) It worked!! But is that an error in the end in the screenshot? Nevertheless, I can open gparted now and I don't know what the heck happened before...

Oh and it seems my bin folder contains a whole bunch of stuff when I do "ls /usr/bin" but when I go to the "cd /usr/bin" directory and do "ls" then that shows only "flash-player-properties" because that is what there is in the folder. My mistake I thought I should be able to see the "whole bunch of stuff" both way! They are not even hidden...so where are they?

Also, as **vasa1** suggested when I did "ls /usr/bin", I couldn't see "gparted" but now that I unistalled and installed I can see "gparted-pkexec" in bin! However, when I check the "usr/bin" without console (how do you say it? GUI way I guess?) I can only see "flash-player-properties" only and nothing else...is it supposed to be like that? Thanks guys, much appreciated!!

---

