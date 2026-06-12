---
title: "Nautilus script to open terminal. Change which terminal?"
date: 2014-09-07
forum: General Help
---

### Post by stretch4 on 2014-09-07
I installed the package *nautilus-open-terminal* which allows me to open a terminal by right-clicking inside the Nautilus window and clicking on "Open Terminal."
What I want to know is, how can I change which terminal it opens? I would like it to open Terminator, but I think it's opening xterm.

---

### Post by azgrel on 2014-09-07
I've found two solutions:
1) Remove gnome-terminal and symlink terminator to gnome-terminal ```
sudo apt-get remove gnome-terminal && sudo ln -s /usr/bin/terminator /usr/bin/gnome-terminal
```
2) [Install nautilus-actions](http://askubuntu.com/a/76946) and configure new script for Terminator

---

### Post by ajgreeny on 2014-09-07
I am sure you could have done what you wantrd by changing settings in Preferred Applications, but it may depend on which DE you are using.

---

### Post by nerdtron on 2014-09-07
> **azgrel said:**
> I've found two solutions:
1) Remove gnome-terminal and symlink terminator to gnome-terminal ```
sudo apt-get remove gnome-terminal && sudo ln -s /usr/bin/terminator /usr/bin/gnome-terminal
```
2) [Install nautilus-actions]("http://askubuntu.com/a/76946") and configure new script for Terminator

I think it would be better not to remove gnome-terminal. You can just rename the program and create a symbolic link to a new terminal just to be safe.

---

### Post by CantankRus on 2014-09-07
**[COLOR="#FF0000"]Edit[/COLOR]** I use nemo as my file manager and this method works
but appears not to work when using nautilus.
------------------------------------------------------------------------------------
 
Reinstall gnome-terminal, remove created links and set terminator as the default **x-terminal-emulator** in alternatives...
```
sudo update-alternatives --set x-terminal-emulator /usr/bin/terminator
```

To reset back to gnome-terminal use...
```
sudo update-alternatives --set x-terminal-emulator /usr/bin/gnome-terminal.wrapper
```

---

