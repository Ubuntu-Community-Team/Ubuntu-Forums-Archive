---
title: "Problem while using Xfce session."
date: 2006-11-25
forum: General Help
---

### Post by aluuu on 2006-11-25
Hey, when I last used Xfce (which I prefer to use), I accidentilly did something (don't know what) that made the menu field in the top of the screen disappear. ](*,)  The bottom field also disappeared. And I don't know what buttons to press or what I should do to get them back, so I would love some help :) 

Thank you

---

### Post by taurus on 2006-11-25
You can always go back to the default by removing ~/.config...

```
xfce4-panel &
-or-
rm -rf ~/.config
```

---

### Post by aluuu on 2006-11-25
> **taurus said:**
> You can always go back to the default by removing ~/.config...

```
xfce4-panel &
-or-
rm -rf ~/.config
```


Where shall I type that? Terminal? If so, can I type it in the GNOME teminal? Sorry for being such a noob. ^^

---

### Post by highneko on 2006-11-25
> **aluuu said:**
> Where shall I type that? Terminal? If so, can I type it in the GNOME teminal? Sorry for being such a noob. ^^
Yes, if you want to recursively force deletion of this file or folder. You could use gnome-terminal.

---

### Post by CoolHand on 2006-11-25
I know I'm not the original poster but yes you could do that in a gnome terminal. Or since you are running XFCE you could try a couple other things.  You could probably run the commands by typing alt - F2 for a run dialog and running it there.  I would recommend a different command first though.  Try *xfce-setting-show* from there you should be able to adjust all your desktop settings.  You could use the xfce4-terminal or you could hit ctrl-alt-*num* (num being 1-6) for one of the standard tty terminals to log in and run the commands.  If you do the same with num 7 it will take you back to the gui.  If you use the rm command then you will have to log out and back in to get back to the default.  What probably happened is you accidentally removed all your panels.  Try getting the settings dialog with the command I suggested and adding a new panel.  Hope that helps.  :)

---

