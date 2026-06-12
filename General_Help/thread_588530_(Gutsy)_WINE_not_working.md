---
title: "(Gutsy) WINE not working"
date: 2007-10-23
forum: General Help
---

### Post by MindSpore on 2007-10-23
I tried installing wine (sudo apt-get install wine), and launching a .exe file, and... nothing happened.  So, I tried again from the command line.. and I get something like this..

"...creating configuration directory /home/spore/.wine/"

and it just sits there and does nothing.  I took a look in my home folder and it creates a folder each time wine is run like "/home/spore/.wine-AJxKvb"  ie. ".wine-" followed by some random letters.  I've tried on several win32 executables, some very simple that I know have worked in the past.  I have also tried running winecfg and it does the same thing.

SO, I uninstalled wine added the winehq gutsy repo and re-installed.  No difference.  I get no errors, it just says it's creating the config directory creates the ".wine-AWkdjaA" directory and does nothing else until I kill it (Ctrl+C).  Those directories seem like the correct structure for a .wine folder, but every time I run it it adds another one, so I have to delete the directory every time or my home folder is flooded with wine config folders.

HELP!?

---

### Post by karth on 2007-10-23
The solution is to remove the .wine directory (provided you save all you want from it before you delete it)
```
sudo rm -r -d ~/.win*
``` (this will remove .wine and all .wine-something under your home dir)

Relaunch your .exe as you did before and it should run.

---

### Post by MindSpore on 2007-10-23
No dice.  I had previously deleted the .wine folders, ran that command anyway to be sure.  Still having the same problem.

wine: creating configuration directory '/home/spore/.wine'...

and nothing after that.

---

### Post by karth on 2007-10-23
You can also try to specify a wineprefix to force wine to use a specific configuration folder (i.e. already created folder)

```
env WINEPREFIX="/home/spore/.wine" wine /path/to/your/app.exe
```

---

### Post by lajevardi on 2007-12-13
that works for me, thanks ;)

---

