---
title: "keeping the desktop icons showing, they dont show sometimes"
date: 2012-12-29
forum: General Help
---

### Post by sdowney717 on 2012-12-29
I typically use gnome-shell and cinamon desktop.
The desktop icons, folders which are in the desktop folder wont display unless I click open the desktop folder, then they magically appear on the desktop.

So what to do? I want them to be there like they used to do.

---

### Post by TheFu on 2012-12-29
I don't use gnome-anything or a DE. No idea, perhaps few questions can help?

Do you have funny characters in the filenames (not part of your locale) or are there a very large number of files? Over 50?

Also, if filenames start with a "." (period), those will not be displayed. There are probably other "special" names that are not displayed too - like "*.desktop"

---

### Post by sdowney717 on 2012-12-29
the odd thing is, they dont show on the desktop, then sometimes they do show on the desktop
Right now they are not showing on the desktop wallpaper.
 
pic shows no icons on desktop for today

---

### Post by sdowney717 on 2012-12-29
I found some info, but I swear I never modified the setting.
I have been trying different theme ideas.
Now I have icons showing.
[http://joesteiger.com/2011/07/02/enable-desktop-icons-and-right-click-gnome-3-gnome-shell-ubuntu-11-04/](http://joesteiger.com/2011/07/02/enable-desktop-icons-and-right-click-gnome-3-gnome-shell-ubuntu-11-04/)

---

### Post by sdowney717 on 2012-12-29
that works for gnome-shell, but not on cinammon 
Mint thread on the same subject
says to get rid of nautilus!
[http://forums.linuxmint.com/viewtopic.php?f=208&t=114299](http://forums.linuxmint.com/viewtopic.php?f=208&t=114299)

```

Re: Desktop Icons not appearing on Cinnamon 1.6.1 at Log In

Postby msoa on Sun Oct 21, 2012 9:10 pm
I think found the solution: (Ubuntu 12.04)
change the following:

Code: Select all
    /etc/xdg/autostart/nautilus-autostart.desktop


to

Code: Select all
    /etc/xdg/autostart/nautilus-autostart.desktop.disabled 
```


HOW would you apply what he wrote?
All I want is for the desktop icons to appear whn booting cinammon,
**Currently you must launch Nautilus, then they will appear.**
I want them to appear at boot.

also more from here
[http://askubuntu.com/questions/84847/how-to-disable-nautilus-from-handling-the-desktop](http://askubuntu.com/questions/84847/how-to-disable-nautilus-from-handling-the-desktop)
> If you install the gnome tweak tool (which you'll want anyway) you can disable file manager handling the desktop. But as far as I know you will then have no desktop icons. Most if not all DEs are structured such that the file manager handles desktop icons.

---

