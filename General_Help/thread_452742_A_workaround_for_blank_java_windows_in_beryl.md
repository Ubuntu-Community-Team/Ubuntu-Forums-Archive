---
title: "A workaround for blank java windows in beryl"
date: 2007-05-23
forum: General Help
---

### Post by Death_Sargent on 2007-05-23
We all know that metacity handles lava as it should so under metacity lava based apps run as they should

well I wanted to automate the switch between metacity and beryl however that is proving quite impossible

first i wrote the code that switches to metacity and runs the program

```
metacity --replace && affinity && reberyl
```

now i then wrote the program reberyl as a way to reinstate the beryl window manager and it looks like this

```
sleep 39
emerald --replace
```

now when i run the first program what happens is metacity replaces then immediately there after beryl (emerald) replaces.

I already made sure beryl was running so that it was not forcing it's window.

now if i remove the line
```
emerald --replace
```

however there is no automatic return to beryl.

what should I do?

---

### Post by srt4play on 2007-05-23
[http://ubuntuforums.org/showthread.php?t=447791](http://ubuntuforums.org/showthread.php?t=447791)

---

### Post by Death_Sargent on 2007-05-23
this fixed the problem 

> **ernz said:**
> Same problem. I tried this, and it didn't work for me. However putting the line:

export AWT_TOOLKIT="MToolkit"

...at the very end of these files:

~/.bashrc
~/.bashrc~    (Note: You might now have this one)
/etc/profile

**...seemed to do the trick**. For those of you who don't know, you will need to edit the /etc/profile file with sudo. You can do this by opening the accessories menu, opening a terminal and typing:

sudo gedit /etc/profile

Also, the ~/ prefix is just your home directory i.e. /home/aaron/ 
The '.' prefix of a filename or directory sets that item to a hidden state. You can view hidden items in nautilus by pressing CTRL+H or View > Show Hidden Items in the menus.

Hope this helps,
Ernz

---

### Post by srt4play on 2007-05-23
cool

---

