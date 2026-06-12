---
title: "[SOLVED] Custom Application Launcher Trouble"
date: 2007-12-02
forum: General Help
---

### Post by Majorix on 2007-12-02
I have just installed foxGUIb (an IDE for fxRuby) and it's launched with this line:
```
cd /home/myUserName/foxGUIb; ruby foxGUIb.rb
```
which cd's to the installation directory and gives ruby the executable file as an argument.

But when I set this in the custom application launcher as a command and select "application" for the type, it says something about it not understanding what cd is. Then when I select "application in terminal" it tries to launch but says
> There was an error creating the child process for this terminal
and shows an empty terminal.

What am I doing wrong? Or is this a bug?

---

### Post by Majorix on 2007-12-02
OK I have fixed it nevermind. Apparently its a bug with gnome-terminal.

---

### Post by mailforbiz on 2008-04-27
> **Majorix said:**
> OK I have fixed it nevermind. Apparently its a bug with gnome-terminal.

I am having the same problem. Can you tell us the way you fixed this?

---

### Post by jsa13 on 2008-07-07
I was having the same issue and it was because I was not using a full path for the executable script.  Make sure you are running "Type: Application in Terminal" and then use the FULL path with no env. variable (like $HOME) or '~' for the Command.

---

