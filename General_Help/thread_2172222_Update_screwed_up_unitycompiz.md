---
title: "Update screwed up unity/compiz"
date: 2013-09-03
forum: General Help
---

### Post by CyrodiilSavior on 2013-09-03
I recently got a new acer m5 ultrabook that i am using for school. I managed to get ubuntu 13.04 working on there fine for the first few weeks. One evening the update manager was driving me crazy so i decided to do the much needed updates. upon a reboot i was greeted by a horror. Once i was logged in my desktop was only that there was no unity and no compiz i managed to open a terminal with ctrl+alt+t and could open applications through nautilus but i cant seem to get unity fixed. Please help, i need this ultrabook and i can only bare windows 8 for so much longer. 

Thanks!

---

### Post by r_avital on 2013-09-03
Well, first, what exactly is the horror that greeted you when you rebooted?

Let's see what the upgrade did:

1. When you log in, do you get a login screen?  Silly question, I know, but let's make sure we have all the info.
2. Do you have a box, off to the left side of the screen, with your user-name in it, asking you to type in the password?  If so, look at the upper-right corner of the box, to the right of the user-name, is there a light dot, or a logo?
3. If so, click it.  Do you get any options after you click that dot or logo?
4. Can you run Synaptic?  If so, go to File>History, it should open up a window with dates on the left pane.  Click on the date of your latest update, and you will see on the right pane, a list of everything installed by the last update.  Can you copy that and paste it in a reply here?

We'll know more then.

---

### Post by CyrodiilSavior on 2013-09-03
yeah i get a login screen everything is fine with the exception of my wifi (which is an issue i fixed when i first installed ubuntu) it's only when i login that it is all fouled up

---

### Post by r_avital on 2013-09-03
1. When you log in, do you have a box, off to the left side of the screen, with your  user-name in it, asking you to type in the password?  If so, **look at the  upper-right corner of the box, to the right of the user-name, is there a  light dot, or a logo?**
3. If so, click it. ** Do you get any options after you click that dot or logo?**
4. Can you run Synaptic? In terminal, run synaptic-pkexec, enter your password.  Go to File>History, it should open  up a window with dates on the left pane.  **Click on the date/time of your  latest update, **and you will see on the right pane, a list of everything  installed by the last update.  C**an you copy that and paste it in a reply  here?**

---

### Post by Yellow Pasque on 2013-09-03
If it was me, I would create a new user, and log in as that user. If Unity works for the new user, chances are that your regular user's Unity config is borked and needs reset. [http://www.ubuntuask.com/q/answers-how-do-i-reset-my-unity-configuration-17610.html](http://www.ubuntuask.com/q/answers-how-do-i-reset-my-unity-configuration-17610.html)

If not, it's probably something with video driver. Post /var/log/Xorg.0.log then (use [ code ][ /code ] tags)

---

### Post by CyrodiilSavior on 2013-09-03
Synaptic isn't installed. And I have no interney connection

---

### Post by CyrodiilSavior on 2013-09-03
And yes I can change the desktop environment from logon screen. Gnome fallback works fine

---

### Post by stinkeye on 2013-09-03
Check to see if compiz is running.
In terminal ...
```
sudo apt-get install wmctrl
```
Then...
```
wmctrl -m
```

Output should show something like...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] wmctrl -m
Name: **Compiz**
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

If compiz is running may just need to re-enable the unity plugin.
```
sudo apt-get install compizconfig-settings-manager
```

In terminal enter ```
ccsm
``` and check the ubuntu unity plugin is enabled.


[COLOR="#FF0000"]EDIT:[/COLOR]
If you have no internet try running...
```
dconf reset -f /org/compiz/ && setsid unity
```
This will reset compiz back to defaults with the unity plugin enabled and reload the window manager.

You can achieve the same result by running just the first part of the command in another session
and then logging back into the ubuntu session...
```
dconf reset -f /org/compiz/
```

---

