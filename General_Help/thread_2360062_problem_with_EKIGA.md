---
title: "problem with EKIGA"
date: 2017-05-01
forum: General Help
---

### Post by hilario_ferreira on 2017-05-01
Hi all

After a first install of ekiga I entered a wrong sip account.

Now whenever I open ekiga to edit my account I don't find the "EDIT" option:

All I have is the webcam icon : contacts icon ; dialpad icon and call history icon-

Uninstalled and reinstall but it always opens with the same menus.

I think that whenever I reinstall the program takes the former configurations which means unisntall was not completely done.

What can I do to fix this ???

---

### Post by howefield on 2017-05-01
Looks for ekiga files/folders in your home folder.

For eg,

```
~/.gconf/apps/ekiga/
```

there may be more than the one in .gconf but finding and deleting them is likely to return you to a freshly installed state.

---

### Post by hilario_ferreira on 2017-05-01
Sorry , but I made a search on my home folder looking for ekiga and there are several folders:
ekiga
ekiga-list
ekiga-dbg-list
ekiga-png
ekiga-postrm etc... etc...
The problem is that I can't eliminate them - I try to delete them but nothing happens !!!

---

### Post by howefield on 2017-05-01
Most of the above look as like they should be in the system folders not the home folder, what's the output of..

```
find ~/ -name "*ekiga*"
```

---

### Post by hilario_ferreira on 2017-05-01
Ok you were right.
the output is : /home/hilario/.gconf/apps/ekiga

I had to make control+H to see hiden folders.


I have just deleted those files and folders and will reinstall ekiga.

tks

---

### Post by howefield on 2017-05-01
> **hilario_ferreira said:**
> I have just deleted those files and folders and will reinstall ekiga.

OK. You don't say how you "*just deleted those files and folders*" but if you are removing a package it is best to use your package manager to do it or from the terminal use..

```
sudo apt remove ekiga
```

to remove the application configuration files along with with the application use purge instead of remove.

```
sudo apt purge ekiga
```

---

