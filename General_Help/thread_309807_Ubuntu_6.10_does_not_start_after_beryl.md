---
title: "Ubuntu 6.10 does not start after beryl"
date: 2006-11-30
forum: General Help
---

### Post by hadiriazi on 2006-11-30
Hi guys;

I followed a guild on how to install beryl in 9 simple steps. After reboot the login page came up. I entered my username and pass. desktop tried to come up with the beryl splash screen but at the moment the splash is gone nothing happens and Im faced with a black screen and a blinking cursor at the top.

Please help me.

Thanks

---

### Post by PriceChild on 2006-11-30
[COLOR=Red][B]Beryl is NOT a beginners subject!
[/B][/COLOR]
Might be an idea to tell us what guide you followed :)

Gnome splash or Beryl splash?

blinking cursor.... X must have crashed, wierd not to give you an error... better post your /etc/X11/xorg.conf also.

---

### Post by hadiriazi on 2006-11-30
Sorry for the post in wrong place

- here is the link to the article I followed to install beryl: [http://ubuntufreak.blogspot.com/](http://ubuntufreak.blogspot.com/)

- Beryl splash

- I cant post /etc/X11/xorg.conf because I cant even login in order to run a terminal

Thanks

---

### Post by PriceChild on 2006-11-30
After discussion over IM, the user has informed me he has edgy with nvidia, so I am advising to undo everything done previously:

ctrl+alt+F1 to get to a cli. (before logging in)
enter username and password.

```
sudo nano /etc/apt/sources.list
```Remove the line you added at the bottom.
one of...```
    deb http://www.beerorkid.com/compiz edgy main-edgy
    deb http://media.blutkind.org/xgl/ edgy main-edgy
    deb http://www.beerorkid.com/compiz edgy main-edgy
    deb http://media.blutkind.org/xgl/ edgy main-edgy
```Ctrl+x to quit, y to accept changes and save.

```
sudo apt-get update
sudo apt-get remove xserver-xgl libgl1-mesa beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
```I think this should do it... If it tries to remove several more packages than listed here such as ubuntu-desktop and xserver-xorg then try it again without the libgl1-mesa. I've just tested it here and it should be fine.
```
sudo rm /usr/bin/startxgl.sh
sudo rm /usr/share/xsessions/xgl.desktop
```
This ***should*** work. However, I take no responsibility if you system goes awry.

Once this is done, you should be able to
```
sudo /etc/init.d/gdm restart
```to get back into gnome and log in.

Once in, go to System>Preferences>Sessions and remove beryl-manager and beryl-xgl from the startup tab.

Restart your computer to make sure everything is fine, then go to [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851) to install :)

---

### Post by hadiriazi on 2006-11-30
i have followed the instructions till:
sudo apt-get update
sudo apt-get remove xserver-xgl libgl1-mesa beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes

executed the command, here is what I got at the end:
E: Couldn't find package beryl-dev

do i ignore and continue?

---

### Post by PriceChild on 2006-11-30
Yup just continue.

---

### Post by hadiriazi on 2006-11-30
I followed the instructions and everything works now.
Thank you very much

going to install beryl the right way now :)

---

