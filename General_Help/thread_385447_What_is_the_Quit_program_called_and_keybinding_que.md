---
title: "What is the Quit program called and keybinding question."
date: 2007-03-15
forum: General Help
---

### Post by otazman on 2007-03-15
Trying to figure out what the Quit program is named/called in 6.1? I am trying to make a keybinding for it. i.e. system monitor program is called gnome-system-monitor

Second question:
Using gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 too bind commands. How do I find the list where the run_command_X shortcuts are listed? Are they stored in a file?

Thanks, 
OT

---

### Post by stylishpants on 2007-03-16
Quit program, I don't know.


To see the run_command list, run gconf-editor and navigate to the location you mentioned.  You can edit the list too with this tool.

---

### Post by aysiu on 2007-03-16
You mean ```
xkill
``` right? Is that what you mean by "the quite program"?

---

### Post by otazman on 2007-03-16
Not the xkill. I mean the default Quit.. program. :^) The one that has a red circle and allows you to "Log off, switch users, lock screen or power down the computer". That is also the description of the Quit button. Sorry I don't know the programs name or what the executable is called. 

OT

---

### Post by aysiu on 2007-03-16
I don't know what the name is, but I have a proposed strategy for you finding it out.

Create a new test user and install *xnest*: ```
sudo adduser test
sudo apt-get update
sudo apt-get install xnest
gdmflexiserver --xnest
``` This will open a new window with a login screen--nested within your regular user's session. At that login screen, log in as the test user. Then, select **Quit** from the panel of the test user's session, but don't actually quit yet.

Go back to your regular user's session and open up ```
gnome-system-monitor
``` Look through all the processes running and see if you can find one that might be **Quit**.

Best of luck, and post back here any results or other obstacles...

---

### Post by otazman on 2007-03-17
That didn't work. Is the Quit menu part of the kernel because I sure don't see anything opening? Any other ideas. The whole reason I ask is this menu is almost identical to Windows Ctrl+Alt+Del and I would like to map the same features.

---

### Post by 23meg on 2007-03-17
> Trying to figure out what the Quit program is named/called in 6.1? 

```
gnome-session-save --kill
```

---

### Post by otazman on 2007-03-18
23Meg you are the Bomb and correct.

Thanks, OT

---

### Post by 23meg on 2007-03-18
You're welcome. Try using the "apropos" command if you have problems figuring out what command does what in the future.

---

