---
title: "Storing terminal sessions"
date: 2012-11-11
forum: General Help
---

### Post by gameguy on 2012-11-11
I usually work on one project at a time, and in that project I like to have certain terminal tans (for example, when working on django projects, I like to have one to run the server, one for apps, one for static files, one for templates, etc) and I like to name them. Is there any easy way to run a set of commands when a terminal starts up (basically, just cd to certain directories and name the terminal tabs for each seperate tab), or if not, is there a command for making a new tab in terminal?

---

### Post by Habitual on 2012-11-12
Not sure about "terminal tans". Perhaps that is "terminal trans(parent)?"

any way, [this]("http://www.bournetoraiseshell.com/article.php/20110525173721873") may help

---

### Post by raja.genupula on 2012-11-12
To open a TAB in terminal , you have ```
SHIFT+CTRL+T
```. I am suggesting you to use something like alias . when you type that single command all the code attached to that will executes .

---

### Post by Cheesemill on 2012-11-12
You can set up your terminal with all of the required tabs configured and then issue a command to save the state of the terminal:
```
gnome-terminal --save-config=.terminalstate
```This will save the state as a file called .terminalstate. If you want to have this file used whenever you start a terminal you can edit the /usr/share/applications/gnome-terminal.desktop file and edit the line that begins Exec= so that it reads:
```
Exec=gnome-terminal --load-config=.terminalstate
```If you want to see exactly what is happening the terminal state file is pretty self-explanatory, you can open it in a text editor and make manual changes to it if you want.

---

### Post by gameguy on 2012-11-13
The save-config and load-config appears to be working great. I can even have a seperate terminal session for each project now :)

Thanks a heap

---

### Post by gameguy on 2012-11-13
Actually, I've just realised that these --load-config options don't store the tab titles. Is there any way to get around that?

---

### Post by gameguy on 2012-11-13
Wait, I found it. Although the save-config doesn't save your terminal title, what you can do is to go into the config file it saved and add Title=<title> as a line to each tab (but you first need to change the profile to keep its old title when a terminal command wants to change it).

Also, I strongly advise this in combination with xbindkeys, because these terminal commands can get quite tedious.

---

