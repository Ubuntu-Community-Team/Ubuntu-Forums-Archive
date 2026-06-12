---
title: "Cannot start PC game."
date: 2022-04-15
forum: General Help
---

### Post by beedee33 on 2022-04-15
Hi all - Hope someone can help with this problem which is driving me mad.  Installed Wine just the other day, took me days to work out how to install "Tiger Woods 2004 with 3 install discs.  Now it's apparently in the .wine folder, but everything I try to get it running fails, message says something like "no Windows association".  I right click the file..."open with other application" >>>>> "Wine windows programm loader", and all it does is open the game files.

What is the procedure for starting a manually installed game PC game?  I've got "winecfg" set to Windows XP.   Any help appreciated.

I'm not really a gamer I only have 3 games, Tiger Woods PGA Tour 2004, the first Medal of Honor, and the first Sniper Elite,,, which if anybodys interested plays flawlessly with the Linux download from Steam for £5 odd.

---

### Post by grahammechanical on 2022-04-15
Try this:

```
wine explorer.exe
```

A Windows Explorer type file manager will open. 

1) Click My Computer.
2) Click Drive C folder
3) Open Program Files folder or Program Files (x86) folder
4) Search for the relevant program folder
5) Open the folder and drill down through the folders until you find the program's exe file and double click it.

If that loads the program it might put an icon in the dock which you can fix to the dock as a favourite which in turn could be used to launch the program. There should also be an icon in the Show applications grid.

Regards

---

### Post by beedee33 on 2022-04-15
Nope, afraid no response or any life from it atall,

I am getting "There is no windows programm configured to open this type of file".

---

### Post by beedee33 on 2022-04-17
Thanks for all the replies....(well one anyway).  Having to take a self learning Degree in Computation here.  Game is 32 bits apparently, and "wine" default install is 64 bit, so need a 32 bit prefix. The Saga continues :-)

---

