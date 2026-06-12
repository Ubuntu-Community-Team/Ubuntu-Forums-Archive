---
title: "Bash won't run scripts automatically from /usr/games"
date: 2007-08-20
forum: General Help
---

### Post by abrichr on 2007-08-20
After installing Planet Penguin Racer, clicking on the icon in Applications->Games results in the error message:  "Could not launch menu item.  Failed to execute process "ppracer" (No such file or directory)"

From the terminal, typing in ppracer yields:

```
The program 'ppracer' is currently not installed.  You can install it by typing:
sudo apt-get install planetpenguin-racer
Make sure you have the 'universe' component enabled
bash: ppracer: command not found

```

Following along with its suggestion:

```
sudo apt-get install planetpenguin-racer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
planetpenguin-racer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The only way to get it running is to navigate over to /usr/games and run ./ppracer.  I'm still not very knowledgeable as to how linux runs commands, but it seems to me that whatever controls shortcut commands (bash?) is not linking properly to the directory /usr/games, as this only happens with games.  All other newly installed programs do not experience the same issue.  Also, I am able to run the default installed games without this problem.

Where can I read about how linux handles shortcuts such as these, and how can I repair this?

---

### Post by lloyd_b on 2007-08-20
What you need to do is add "/usr/games" into your "path".  The path provides a list of directories to search when you type in a command.

Edit the file "~/.bashrc", and add the following line:
```
PATH=$PATH:/usr/games
```

Note: you'll need to close the current terminal window (or log off, if you're logged into a console session) before the changes take effect.  You can also type that command in a terminal window and get the same effect, but only for that terminal window.

Lloyd B.

---

### Post by abrichr on 2007-08-20
Alright, so now running "ppracer" from the console works, but I still get the same error message when I click on the entry in the Applications->Games menu.

---

### Post by stchman on 2007-08-20
> **abrichr said:**
> Alright, so now running "ppracer" from the console works, but I still get the same error message when I click on the entry in the Applications->Games menu.

In the menu entry enter the FULL path of your game.

---

### Post by abrichr on 2007-08-20
...well obviously that'll work.  But my problem is that when I install a game, the default menu item doesn't work.  It's silly to have to reset the shortcut every time I install something.

---

### Post by lloyd_b on 2007-08-20
Have you tried logging completely off and then back on?  The changes to .bashrc affect new terminal windows, but they won't affect the main session until you log off.

Lloyd B.

---

### Post by abrichr on 2007-08-20
Yes, I've tried restarting too, still the same error.

---

