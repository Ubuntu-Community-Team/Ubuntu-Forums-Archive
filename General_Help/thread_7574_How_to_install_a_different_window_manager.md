---
title: "How to install a different window manager?"
date: 2004-12-08
forum: General Help
---

### Post by RoD on 2004-12-08
I wanna use other window manager ('cause my computer it's a bit old). I've installed enlightenment with synaptic (with no errors) and i can't log with it. I don't have the option to chose it when gdm appears when I start my pc. What should I do to use other window manager like enlightenment or icewm?

---

### Post by sertmann on 2004-12-08
While we're at it, i could need some help with trying out Waimea 

installed it via apt, so i'd just like to try and get it started to see what the fuzz is all about

Should be in /etc/gdm/Session but i haven't been able to make a script starting, which googling suggests is the way.... i have a Waimea file in that directory btw

---

### Post by mrosenlof on 2004-12-10
I'm not sure just the window manager will make a big difference if you're looking for something that has lower overhead.  

If you want a more lightweight desktop environment, you should try xfce.  It's in the universe.

apt-get install xfce4

should do it for you.  Select xfce under 'session' in the gdm login greeter.

---

### Post by RoD on 2004-12-10
It's what I've done. Thanks. But I want to try other environments to compare with. My doubt is why xfce4 appears at the gdm menú and not enlinghtenment?
About xfce4 I can say it's nice, but I've some troubles. I've downloaded xfce4-showdesktop-plugin and it doesn't appear anywhere y can't put it in the same way as with others (for example battery plugin). Anyone use's it?
Thanks .

---

### Post by jaclayton on 2005-05-27
Just been having this trouble myself - don't know if you fixed your problems, but...

Find the directory containing all the *.desktop files for the window managers.  Mine was
```
/usr/share/apps/kdm/sessions/
```
Then, as root, copy the .desktop file for the window manager of choice into:
```
/usr/share/xsessions/
``` 
Now when you log out of your current xsession, the menu will contain the usual Failsafe, Default and KDE options *and* the one you just added.

Share and enjoy.

---

