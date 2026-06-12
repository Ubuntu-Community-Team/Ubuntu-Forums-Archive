---
title: "Can't See Files For App"
date: 2014-10-28
forum: General Help
---

### Post by Mike_Karpinski on 2014-10-28
I downloaded GIMP from the software center and I can't view the files inside of it to add enhancements (specifically the re-synthesizer). It's really annoying and probably an easy fix. However, whenever I search GIMP in my computer only the application comes up and under files only my edited pictures. Thanks for the help!

---

### Post by steeldriver on 2014-10-28
Hello and welcome to the forums

AFAIK the usual location for GIMP plug-ins would be either

```

$HOME/.gimp-<version>/plug-ins/

```
for per-user plug-ins, or
```

/usr/lib/gimp/<version>/plug-ins/

```
for site-wide plug-ins, where <version> is the version number that you installed e.g. 2.8 etc.

---

### Post by Mike_Karpinski on 2014-10-28
When I type either of those in, with the version 2.8.14 and 2.8 (exactly what I typed was $HOME/.gimp-2.8.14/plug-ins/), I just get an internet symbol that leads me to a dead link. I can't find any files for GIMP at all, only the app. Do you have any ideas for how I can even look at the files and try to explore from there? Or maybe alternate ways to download it to see the files?

---

### Post by Mike_Karpinski on 2014-10-28
Also new to the forums. Not sure if I had to reply specifically to your message for you to be notified I replied. Any help would be awesome!

---

### Post by steeldriver on 2014-10-28
How exactly are you trying to access the directory? what do you get if you open a terminal (Ctrl-Alt-t)and type

```

ls ~/.gimp-2.8/

```

---

### Post by deadflowr on 2014-10-28
Seems like you might have been trying to search for the files using the Ubuntu menu system commonly known as the dash.
The dash does not list or even look for hidden folders or files.

One option already given is to use the terminal.
Another would be to use the file manager, known as Files (in Ubuntu 14.04;formerly known as Home Folder in older versions of Ubuntu)
In Files press the keyboard buttons ctrl and the letter H at the same time. This will enable the "Show Hidden Files" feature.
(You can also access the feature by going to the menu(Ubuntu puts menus on the top panel; they are hidden until you mouse over them)
The menu listing is View >> Show hidden files.

Hope that helps, a little.

---

### Post by Mike_Karpinski on 2014-10-29
Ctrl H works! Thanks so much :)

---

