---
title: "Font size within Terminal"
date: 2014-06-08
forum: General Help
---

### Post by makaha2 on 2014-06-08
I've recently installed Lubuntu 14.04 on my VERY old computer (circa 1997) and it's going very well. Tried many different distros, and spins, and this works best on this old box!

One issue I do have is the font size within a Terminal session - my eyes are much older than the computer! Is there a way to increase font or text size within a Terminal session? I looked around but could find a specific preference setting for making such a change.

---

### Post by bapoumba on 2014-06-08
By "terminal session", do you mean when you open the terminal or when you log in in a tty with <ctrl><alt><F1> for ex ?
Terminal application :
Open LXTerminal > Edit > Prefs > you can set the font size here.
TTY :
```
sudo dpkg-reconfigure console-setup
```

You can have a read here, as it appears there is some tweaking to do to make it permanent for the TTY :
[http://ubuntuforums.org/showthread.php?t=2210269](http://ubuntuforums.org/showthread.php?t=2210269)
[http://ubuntuforums.org/showthread.php?t=2199051](http://ubuntuforums.org/showthread.php?t=2199051)

---

### Post by makaha2 on 2014-06-08
It's when I go System Tools/XTerm

---

### Post by bapoumba on 2014-06-08
Ah, if you are using Xterm : <ctrl><right click> in an xterm window, you will have the option to change font size.

---

### Post by makaha2 on 2014-06-08
Fantastic. Exactly what I needed, many thanks :P

---

### Post by bapoumba on 2014-06-08
You are most welcome :)
Please mark your thread as solved (under Thread tools), thanks.

---

