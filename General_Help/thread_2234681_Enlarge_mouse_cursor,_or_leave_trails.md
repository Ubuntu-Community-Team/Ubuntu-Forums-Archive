---
title: "Enlarge mouse cursor, or leave trails?"
date: 2014-07-16
forum: General Help
---

### Post by SimonHGR on 2014-07-16
Hi all,

I have a newish machine that has an absurdly high pixel density, and my eyes aren't what they used to be. I find that I lose track of where the mouse cursor it, particularly when I'm using a two monitor setup to drive a projector for presentations and I'm not sure which monitor the mouse is even on.

I would like to have the moving cursor grow, flash, leave trails, or something that makes it much easier to spot. I think I once knew how to change the base cursor, but that won't cut it, as the most common problem is when I have a big console window, and that, of course, changes the cursor to an i-beam, which is even more difficult to see.

Any suggestions? I tried looking in the accessibility settings, and the mouse  settings, but couldn't find anything useful.

Cheers,
Simon

---

### Post by ibjsb4 on 2014-07-16
Maybe try a different cursor theme.  I find crystalcursor easier to see, there is also big-cursor.  Both are in the software center.

---

### Post by grumblebum2 on 2014-07-17
You can enable the ctrl key as a cursor locator.
Mouse radiates when the ctrl key is pressed and released.
[ATTACH=CONFIG]254786[/ATTACH]
Enable via terminal....
```
gsettings set org.gnome.settings-daemon.peripherals.mouse locate-pointer true
```

The default cursor size is 24.
You can install cursor themes of larger size.
I've attached 3 examples...
[LIST]
[*]Large black cursor
[*]Large white cursor
[*]Large white cursor with green glow
[*]
[/LIST]



Extract large-cursors.tar.gz and move the three theme folders to **/usr/share/icons**

To test a theme, open a terminal and choose **one** of the following to enter.
(The same terminal must remain open to enter the next set of commands.Choosing **CURSOR=DMZ-White** will set back to default)
```
CURSOR=DMZ-Black-Medium
CURSOR=DMZ-White-Medium 
CURSOR=DMZhaloG48
CURSOR=DMZ-White
```

Now enter all 3 of these commands...
```
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
```
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20
```
```
sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```
**Log out and back in**.

---

### Post by SimonHGR on 2014-07-17
Many thanks gang, I'll give these a try, they look like great options...

---

