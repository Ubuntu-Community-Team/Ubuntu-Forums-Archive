---
title: "Nautilus Scripts"
date: 2013-04-21
forum: General Help
---

### Post by Geothermal123 on 2013-04-21
I am running 13.04 and I found the .local/share/nautilus/scripts folder, and I put some scripts in there but it's not showing up in a right click menu. How do I access my scripts?

---

### Post by GameX2 on 2013-04-21
You have to make the scripts executables.  Right click on them, "Proprieties".  Select the tab "Permissions", then check the box "Allow executing this file as a program".

I don't know about the ".local/share/nautilus/scripts", but on my system, I put them in ".gnome2/nautilus-scripts".  I assume ".local/share/nautilus/scripts" is for all users, probably.

Tip: You can also add folders in the Nautilus-Scripts folder, to organise your scripts better, in your right-clic menu.

---

### Post by pfeiffep on 2013-04-21
> **Geothermal123 said:**
> I am running 13.04 and I found the .local/share/nautilus/scripts folder, and I put some scripts in there but it's not showing up in a right click menu. How do I access my scripts? 
In a terminal ( access by Ctrl-Alt-t) type```
 ls -al
``` this will display all of your files and folders in your home location. The [SIZE=4]**.**[/SIZE] in front of a file or directory designates it as hidden.

If you wish to use nautilus to view hidden files look for the arrow pointing down (upper right of nautilus) click on it and choose ```
Show Hidden Files
```

This post is also helpful
> [COLOR=#000000]GameX2[/COLOR]
[COLOR=#000000][INDENT]**Re: Nautilus Scripts**
You have to make the scripts executables. Right click on them, "Proprieties". Select the tab "Permissions", then check the box "Allow executing this file as a program".
[/INDENT]
[/COLOR]


---

### Post by zero2xiii on 2013-04-21
+1 for the above.

Rather place scripts in:

~/.gnome2/nautilus-scripts

and remember to make them executable.

Cheers

---

