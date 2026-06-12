---
title: "creating a logout button on my desktop"
date: 2007-11-17
forum: General Help
---

### Post by SunnyRabbiera on 2007-11-17
alright for my husband I have to ask this question.
On his computer he wants to have a logout button on his desktop that will trigger the logout sequence just in case the gnome panel fails to load.
I have told him how to logout in the terminal but he wants an easier way to do it.
so can anyone help me on this?
he is using Ubuntu gutsy with gnome

---

### Post by shad0w_walker on 2007-11-17
I don't know the way to run it from console but as you know the command, just right click on the desktop and create a launcher, for the command just put in what he would need to run from the terminal.

---

### Post by SunnyRabbiera on 2007-11-17
well the command I use is "shutdown" or "reboot"
but he needs something that will load gnomes logout manager instead of just shutting down the whole computer.
he honestly needs a button on his desktop that will activate gnomes logout manager and I have no idea what its called

---

### Post by shad0w_walker on 2007-11-17
This command might work. 

gnome-session-save --kill

It should save the session and logout the user.

---

### Post by SunnyRabbiera on 2007-11-17
actually it really doesnt, I have tried it but nothing happens.

---

### Post by shad0w_walker on 2007-11-17
Did you try running it from the terminal or just create the launcher? If you made the launcher, make sure you select the type of application as Application in Terminal.

---

### Post by SunnyRabbiera on 2007-11-17
well i did it just now and it seems to work...
I tried that command in the terminal but nothing happened though

---

### Post by shad0w_walker on 2007-11-17
Strange it doesn't work from the terminal, but if the shortcut works then I suppose it doesn't make much difference, as long as it does what you need.

---

### Post by SunnyRabbiera on 2007-11-17
yeh.
but I also need this working for something else as well.
To help my husbands transition from windows to linux I installed the mint menu, the package worked but I had to edit it here and there but in tiny little ways.
the bad news is that the quit button does not work in it, it seems to have the same command listed above in it (gnome-session-save --kill) but that doesnt seem to do a thing.
I have a logout app on his panel to help him but he wants to do this from the menu...
maybe I should take this one over to the linux mint forums?

---

### Post by shad0w_walker on 2007-11-17
I'm afraid i have zero knowledge of linux mint so probably best to try over on their forums.

---

### Post by SunnyRabbiera on 2007-11-17
yeh, well I would give him mint but that will just confuse him...

---

### Post by KIAaze on 2007-11-17
In the worst case, you can always try a radical gdm restart (same effect as ctrl+alt+backspace):
```
sudo /etc/init.d/gdm restart
```

In the end, it's as if you logged out. ^^

Only problem is that it requires sudo permissions... :/
Well, ctrl+alt+backspace should do the trick, altough it's not very nice.

---

