---
title: "Making program to run terminal commands"
date: 2016-02-15
forum: General Help
---

### Post by jordan62 on 2016-02-15
Hello

I'm new to Ubuntu I have installed teamspeak 3 and to run it I must go to the directory ~/Programs/teamspeak\3/. Then I must run the .sh to start teamspeak.
with ./program.sh

which then start teamspeak, I was wondering is there a way to make a program or something i can double click which will start teamspeak 3 something that executes a string of terminal commands?

---

### Post by ian-weisser on 2016-02-15
You can create a .desktop file,which will create a clickable icon and run whatever you wish
Lots of examples are in /usr/share/applications and ~/.local/share/applications
Store your own creations in ~/.local/share/applications

---

### Post by Dennis N on 2016-02-15
You could create a bash script to start your program and save it in ~/bin. Make it executable. Then, create a symbolic link to the script on the Desktop to start it.

Actual example: script to start the game Machinarium (script saved as machinarium in ~/bin):
```
#!/bin/bash
#play Machinarium
cd /home/dmn/games/Machinarium
./Machinarium

```

Create symbolic link on the Desktop to click and run the script:
```
[dmn@Sydney ~/bin]$ ln -s ~/bin/machinarium ~/Desktop/Play_Machinarium
```

---

