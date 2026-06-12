---
title: "Trying to change this forever"
date: 2008-05-02
forum: General Help
---

### Post by djmoore85 on 2008-05-02
Alright, I have been trying for an hour to get this to work, and am stumped. After the login screen, when I hit enter, I get a screen that is the Ubuntu human theme color, and then the desktop loads up. I thought this was the splash screen, so I downloaded a new one from GNOME-art, but it is only a small centered portion that got changed on this screen. My question is this: how do I change this color to suit the overall color scheme that I have for my desktop? I know it has to be something simple that I am just overlooking. Thanks in advance

---

### Post by ACMiller on 2008-05-02
What about system > administration > login window. Click on the local tab, and change the background color which appears half way down that window.

Hope that helps

---

### Post by djmoore85 on 2008-05-02
Negative, I tried that before thinkin the same thing, but it changes the background color used before the login window appears rather than the post-login

---

### Post by PinkFloyd102489 on 2008-05-02
System > Preferences > Appearance > Backgrounds tab


Change the color at the bottom.

---

### Post by djmoore85 on 2008-05-03
Also a negative on that, I tried that before to give it a horizontal gradient but nothing changed with the splash screen. This is a real stumper ain't it?

---

### Post by FuturePilot on 2008-05-03
Are you using Gutsy?

---

### Post by djmoore85 on 2008-05-03
Yes I am still using Gutsy, I have decided to wait until a few more bugs are worked out or solutions found to before I upgrade to hardy.

---

### Post by FuturePilot on 2008-05-04
There's a bug in Gutsy with the background color after GDM login. There's a workaround for it.
```
gksudo gedit /etc/gdm/PreSession/Default
```
Find the line that says 
```
BACKCOLOR="#DAB082"
```
and change the hex color (#DAB082) to whatever color you want. It must be in hex though.

---

### Post by djmoore85 on 2008-05-04
Appreciate it man, so to what I understand there is no way to make it a gradient, and if I change the scheme down the line I will need to go back and do the same process? Thanks again for the help

---

### Post by FuturePilot on 2008-05-04
No problem. :)
I don't think it's possible to set a gradient as far as I know. Yes, if you want to change the color again at some point you need to change it manually in that file. But the good news is it is fixed in Hardy. :)

---

