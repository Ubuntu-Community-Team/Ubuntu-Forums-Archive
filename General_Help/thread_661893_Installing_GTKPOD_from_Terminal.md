---
title: "Installing GTKPOD from Terminal"
date: 2008-01-08
forum: General Help
---

### Post by zutronius on 2008-01-08
I am trying to install gtkpod through terminal on my laptop. I would normally do it under the Package Manager,  but I am in Europe and without an internet connection. I managed to go to a cafe and download the program and burned it onto a cd.

I am still a new Ubuntu user and would like it if someone could tell me the terminal commands required to install gtkpod from the burned cd. If anyone could help me, that would be grand. :)

---

### Post by Tenken on 2008-01-08
What format is the file that you downloaded? If it is a .deb file like [this one]("http://www.getdeb.net/app.php?name=gtkpod"), use this command

```
cd /path/to/deb/file
dpkg -i filename.deb
```

or double click the .deb in the GUI.

If you have the source file (filename.tar.gz, probably) it is a little more complicated, if it is let me know I'll try to help you out.

---

