---
title: "Customizing desktop menus"
date: 2008-07-04
forum: General Help
---

### Post by ceclauson on 2008-07-04
Hello!

I'm trying to add a launcher to Games menu (specifically for Boswars).  This is the first time I've tried it, and it doesn't seem to be working.

I can add the icon along with the path of the target (right click menu, choose submenu, give a name and browse to the application), but when I click the icon in the menu, nothing happens, i.e. the application doesn't run.  It seems to be finding the application, because when I tried moving it to a different place than where the launcher should find it, and tried launching it, I got an error message about not finding it.  So because I'm not normally getting this error message, I guess the launcher is finding the application, but it's just not launching it.

Extra info: the application is executable.  I can launch it both from the command line and with a double click from nautilus.  There are two files I can use to launch it.  One is the binary, the other is a shell script I wrote that launches the binary with the right command line options.  I've experimented with having the menu launcher launch both, and in both cases a got the same result: nothing happened.

Thanks in advance,

Cooper

---

### Post by ceclauson on 2008-07-05
Just posting something else so that the thread moves higher on the list.

---

### Post by benign on 2008-07-05
You need to cd to the directory of the executable in your script...

#!/bin/bash
cd /go/here/toexecute
./execute

if the app is dependent on other stuff it doesn't seem to work if you just do a "/go/here/toexecute/execute/"

---

### Post by ceclauson on 2008-07-16
Thanks for your response.

I added the cd command to the script, and made the executable target absolute, but it still doesn't work.  Also, when the target of the launcher is the executable itself instead of the script, it still doesn't work.

---

### Post by Ryadt on 2008-07-16
Did you try to create a launcher to run the terminal command? If not try it and see if it works. Right click on desktop > create launcher > in type chose application in terminal > then input the terminal command.

---

