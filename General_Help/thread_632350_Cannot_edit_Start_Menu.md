---
title: "Cannot edit Start Menu"
date: 2007-12-05
forum: General Help
---

### Post by Konvert on 2007-12-05
HI guys, Vista convert here, still getting the hang of Ubuntu, my problem is whenever I right click the start icon, then click edit menus, I get a program starting with the title "Starting Main Menu" then it disappears. This same effect happens if I try to run the program via System > Preferences > Main Menu.

Any help would be awesome...

Thanks

K

P.S. Whats the script with Ubuntus caps lock running slow? What I mean is as I am typing when I hit the caps lock on then off it usually still capitalises the next letter, almost as if its running slow i.e. **U**buntu would be **UB**untu, is this a common thing or can I change it?

---

### Post by Konvert on 2007-12-05
Bumpty bump!!! :)

---

### Post by metalheart on 2007-12-05
Start terminal (From Applications -> Tools -> Terminal) and type alacarte and press enter. Do you get any errors?

---

### Post by Konvert on 2007-12-05
> **metalheart said:**
> Start terminal (From Applications -> Tools -> Terminal) and type alacarte and press enter. Do you get any errors?

Hey Metalheart, thanks for the response;

When I type alacarte in terminal I get;

[I]/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
ImportError: No module named Alacarte.MainWindow[/I]

---

### Post by drs305 on 2007-12-05
Check out this link:
[http://ubuntuforums.org/showthread.php?p=3675174](http://ubuntuforums.org/showthread.php?p=3675174)

The solution was changing some messed up permissions in his home folder. Maybe that will fix your similar problem.

Good luck.

---

### Post by metalheart on 2007-12-05
Try to reinstall alacarte
```
sudo apt-get --reinstall install alacarte
```

---

### Post by Konvert on 2007-12-05
> **metalheart said:**
> Try to reinstall alacarte
```
sudo apt-get --reinstall install alacarte
```

Tried the other solution with no success, was tinkering around then decided to see if any new solutions were posted, saw this one, tried it and...

YAY worked, you are a hero my friend, an absolute hero!!!

Thanks! :)

---

