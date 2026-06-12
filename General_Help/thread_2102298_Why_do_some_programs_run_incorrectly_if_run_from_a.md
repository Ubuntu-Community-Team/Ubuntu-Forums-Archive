---
title: "Why do some programs run incorrectly if run from a shortcut or dock/launcher?"
date: 2013-01-06
forum: General Help
---

### Post by blackdalek on 2013-01-06
Can someone explain to me why the program WordBiz runs fine from the terminal but if launched from the side dock or a launcher icon on desktop, the program runs with no sound and no images?

Program is in java from here - [http://www.isc.ro/linux/download.html](http://www.isc.ro/linux/download.html)

Command typed into terminal to run it is -
java -jar wordbiz.jar

...and that works fine.

But if I enter the same command into a launcher, the program runs but with no images or sound.


Why is this?

---

### Post by dcstar on 2013-01-06
> **blackdalek said:**
> Can someone explain to me why the program WordBiz runs fine from the terminal but if launched from the side dock or a launcher icon on desktop, the program runs with no sound and no images?
......
Why is this?

Because a user shell is a different environment from a launcher icon.

---

### Post by blackdalek on 2013-01-07
ok... is there any way to create a launcher for this game which will result in the game running correctly? Or do I have to manually start it through a command line every time?

---

### Post by blackdalek on 2013-01-07
I've come up with a sort of solution. The problem with the launcher seems to stem from the fact that the java app must be run from the directory where the app is located.

Learned about making bash scripts (never touched them before). Made a script thus -
```

#!/bin/bash
cd /home/dalek/WordBiz
java -jar wordbiz.jar
```

and saved as wordbiz.sh on the desktop

Now I can click this and the game will run properly, however it isn't perfect as I get a "Do you want to run "WordBiz.sh", or display its contents?" prompt every time.

So if someone can tell me how to bypass the prompt that would be cool.

---

### Post by efflandt on 2013-01-08
Launchers often have trouble with parameters, so try sh -c and enclosing the rest in single quotes:
```
sh -c 'java -jar wordbiz.jar'
```However, depending where wordbiz.jar is, you likely need to provide a path to it.

For example I use this in a launcher for minecraft (launched in a terminal and that launches the gui):
```
sh -c 'java -Xmx2G -Xms1G -cp ~/MC-client/minecraft.jar net.minecraft.LauncherFrame'
```

---

