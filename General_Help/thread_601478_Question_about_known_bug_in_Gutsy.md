---
title: "Question about known bug in Gutsy"
date: 2007-11-03
forum: General Help
---

### Post by Hagar55 on 2007-11-03
I also have the delay when I boot into Gutsy wich is described in this post:
 Re: Gutsy takes soooo long to bootup
Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024
yres=768

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

Code:

sudo update-usplash-theme usplash-theme-ubuntu

Now it does read 
xres=1024
yres.768
My screens resolutions is 1280x1024

How do you change the setting ?
When I open the file and change the values I cannot save it because I don't have the rights to do so.....sorry knew to Ubuntu and linux.
Should I change the value trough the terminale ?
And if so what command should I use ?

---

### Post by mahousaru on 2007-11-03
```
sudo gedit /etc/usplash.conf 
```

---

### Post by tact on 2007-11-03
to edit any system file you have to do it as the "root" user...  

in a terminal type
sudo gedit /etc/usplash.conf

Now when you make the edits/changes you will be able to save.

("sudo" gives temporary admin powers to any command it is used with (in the above case  -  an editor).

---

