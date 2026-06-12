---
title: "No Splash or GUI on startup"
date: 2008-02-10
forum: General Help
---

### Post by Buntu.Bro on 2008-02-10
Last night while I was playing around with the theme manager and resolution controls and now on bootup I have no GUI or splash. 

It gets crazier b/c I can actually hear the logon sounds of ubuntu but I can see the splash. The I type my username and pw and I can hear the system logon. But all I get is the default tan background with lots or blinking white lines. Does anyone know what I have done? Im thinking it has more to do with the resolution but does anyone have any suggestions.

** The laptop is for school and I dont want to reinstall because I am away from home and dont have the disk and have a ton of papers, resumes, and bookmarks that I need.. any and all help is appreciated. :)

---

### Post by overdrank on 2008-02-10
> **Buntu.Bro said:**
> Last night while I was playing around with the theme manager and resolution controls and now on bootup I have no GUI or splash. 

It gets crazier b/c I can actually hear the logon sounds of ubuntu but I can see the splash. The I type my username and pw and I can hear the system logon. But all I get is the default tan background with lots or blinking white lines. Does anyone know what I have done? Im thinking it has more to do with the resolution but does anyone have any suggestions.

** The laptop is for school and I dont want to reinstall because I am away from home and dont have the disk and have a ton of papers, resumes, and bookmarks that I need.. any and all help is appreciated. :)

HI and welcome, you can try and use the keys ctrl, alt, F1 all at the same time and this will bring your to a command prompt. Login and then reconfigure your xorg with this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Hope this helps and good luck!

---

