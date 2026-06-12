---
title: "Gdm consistent background."
date: 2007-06-01
forum: General Help
---

### Post by whiterussian on 2007-06-01
I have set my gdm background to match my desktop background (In ubuntu feisty), and noticed that between my gdm session and desktop session, the screen is drawn a solid colour, and then my background is reloaded. I'd prefer if the background was constant...

 I've been editing the scripts in /etc/X11/gdm removing anything that looks like an xsetroot or setting the background colour. This worked for me on old vanilla debian; however in ubuntu I've only managed to crash gdm a couple of times.

Anyone more familiar with gdm care to shed some light? I'm relativly certain im editing the right place, I'm just missing the right piece.

---

### Post by snobel on 2007-06-06
If you are referring to the colour of the plain background that appears between the login screen and the desktop background, try changing it through the menus: System/Administration/Login Window/Local tab.

---

### Post by strabes on 2007-06-06
snobel: He wants that background color to not appear at all.

---

### Post by snobel on 2007-06-06
OK, that is harder... 

I have a very dark theme installed, with matching login, splash screen and background. So that interval of ubuntu brown annoyed me as well... I just set the colour mentioned above to black, now I don't notice it anymore.

---

### Post by whiterussian on 2007-06-06
I can set the colour all I want, in fact I've even det my splash screen to my background image, and broke it down more. It seems before my splashsceen displays a command runs that sets the colour and immediatly after as well. The goal would be to find these commands, i assume something like xsetroot, and nuke em'. I've found them easily enough in debian, but havn't been so lucky with ubuntu. When i have more time I'll look again and I'll post any results I find.

---

