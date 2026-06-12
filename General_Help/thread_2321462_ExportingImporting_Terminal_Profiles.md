---
title: "Exporting/Importing Terminal Profiles"
date: 2016-04-22
forum: General Help
---

### Post by agrayray on 2016-04-22
Does anyone know how to export and import terminal profiles?

I have quite a lot of custom colored terminal profiles on my Ubuntu 14 machine that I want to move and import into my Ubuntu 16 machine.

?

---

### Post by QDR06VV9 on 2016-04-22
I use this command to save my current terminal profile settings:

```
gconftool-2 --dump '/apps/gnome-terminal' > gnome-terminal-conf.xml
```

And this command to load profile settings:

```
gconftool-2 --load gnome-terminal-conf.xml

```
[B]NOTE: 
It may be the case that some settings simply won't work in newer versions.
Just to be aware of.
[/B]Regards

---

