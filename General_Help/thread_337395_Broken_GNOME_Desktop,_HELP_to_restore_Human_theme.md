---
title: "Broken GNOME Desktop, HELP to restore Human theme"
date: 2007-01-12
forum: General Help
---

### Post by xthaparian on 2007-01-12
HI Guys

I recently compiled GTK2+ theme for Gnome.

After compiling the theme I selected it from Gome theme manager, but as soon as I selected this themes, my Gnome-panel and Gnome broke and gave me error and after ignoring and canceling the error message, I still get same message and Its like a circular error message.

I dont have access to my terminal and anything in gnome as the error message is continous.


Can seomeone HELP me restore my Gnome theme to Ubuntu-Human default????



](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by jem7v on 2007-01-12
How about you go into a virtual console by pressing Ctrl+Alt+F1, and then navigate to your ~./themes directory, then back up and delete the theme?  I believe the code for that should be something like

```
cp themefile newfilename
rm themefile
```
(where themefile = the theme file you need to get rid of and newfilename is the name of your backup copy)

If you can't get into a virtual terminal, you could try to reboot in Recovery Mode or Failsafe mode or whatever it's called and then do it that way.

---

### Post by xthaparian on 2007-01-13
I saw that its a Contol Panel not a theme which I compiled.

I have only One user defined theme and it is fine as I was working with it without problem.

Its only after I installed this window control, that gnome-panel is crashing..

ANy ideas where I can find the "Theme Details ---> Contol" through command line and change the contol to Human?

---

### Post by jem7v on 2007-01-13
The list of things under "Control" in the Theme Details dialogue ARE GTK2 themes, and they're located inside your ~/.themes directory.

Another thing you might try: There is a hidden file in your home folder named .gtkrc-2.0 that you can open in a text editor.  It will say something like this:
```

# -- THEME AUTO-WRITTEN DO NOT EDIT

include "/home/bryce/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT

```

Back up this file, and then in the original file replace the middle line with:

```
/usr/share/themes/Human/gtk-2.0/gtkrc
```

Then restart Gnome and see if that changes it back to the Human theme.  It might, it might not.  I'm not entirely sure how that file works.

---

