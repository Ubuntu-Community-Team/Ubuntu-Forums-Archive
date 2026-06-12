---
title: "Change File Manager to single click?"
date: 2012-10-25
forum: General Help
---

### Post by acidblue on 2012-10-25
How do I change file manager behavior in 11.10?
I want to open files and folders with a single click.

Also How do I install different theme?
I have the tweak tool already installed but not sure where to put my 
theme files.
I have a .themes folder in my home directory, is this right?
I have a theme in there that I downloaded and extracted but it's not showing up in the tweak tool.

---

### Post by Moose on 2012-10-25
Go to System Settings > Mouse and change mouse action to double click. I think thats how it works. TBH i havent used Ubuntu in a while. (Dabbling in the world of Puppy and Fedora atm) .. and yes themes go in .themes / icons go in .icons.

---

### Post by stinkeye on 2012-10-25
Use [**_[COLOR="DarkRed"]GTK 3.x[/COLOR]_**]("http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=99612091089e00fd5597cfa321d0f5e4") themes.

Change to single click in nautilus preferences.

---

### Post by acidblue on 2012-10-26
Great thanks!
But now how do I get the window buttons, max,min,close, on the right side?
What ever theme I chose they are all on the left and I hate that!

---

### Post by stinkeye on 2012-10-26
In the terminal....
```
gsettings set org.gnome.desktop.wm.preferences button-layout menu:minimize,maximize,close
```

To change back to the default left use...
```
gsettings **reset** org.gnome.desktop.wm.preferences button-layout
```

---

### Post by acidblue on 2012-10-26
Getting error:
No such schema 'org.gnome.desktop.wm.preferences'

---

### Post by stinkeye on 2012-10-26
> **acidblue said:**
> Getting error:
No such schema 'org.gnome.desktop.wm.preferences'

Sorry missed you were still using 11.10.
Settings are still in gconf I think.

Try...
```
gconf-editor /apps/metacity/general/button_layout
```

and change the value to...
```
menu:minimize,maximize,close
```

---

### Post by acidblue on 2012-10-26
Thanks that did the trick :)

---

### Post by stinkeye on 2012-10-26
> **acidblue said:**
> Thanks that did the trick :)

No problem.
The themes you use can dictate the position of the buttons so if you change themes regularly you may have to set the key again or set it as [**_[COLOR="DarkRed"]mandatory[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10602275&postcount=5").

---

