---
title: "[SOLVED] Using Gnome to Execute From a Specific Directory"
date: 2007-09-25
forum: General Help
---

### Post by aaaantoine on 2007-09-25
I have a windows program that breaks if i execute it anywhere from outside its own directory.  How can I make a Gnome panel icon execute this program as if I were in that directory?  I should specify: How can I execute it as described *without using the terminal*?  If the terminal is involved in the initial configuration, I have no problem with that.

Also, what directory does Gnome launch applications from by default?

---

### Post by raijinsetsu on 2007-09-25
Firstly, you can't directly invoke Windows programs from Gnome. You have to use Wine or Cedega.
Secondly, if you're invoking wine, you can set the working directory to be whatever directory the executable is in (ie "/home/YourName/.wine/c_drive/Program\ Files/Some\ Developer/")

---

### Post by mcduck on 2007-09-25
You could create a script that moves you into correct directory & starts the program, and then set your launcher icon to run that script:

```
#! /bin/sh

cd /path/to/your/programdir/
wine yourprogram
exit
```

---

### Post by aaaantoine on 2007-09-26
> **mcduck said:**
> You could create a script that moves you into correct directory & starts the program, and then set your launcher icon to run that script:

```
#! /bin/sh

cd /path/to/your/programdir/
wine yourprogram
exit
```

That did the trick.  Thanks!

---

