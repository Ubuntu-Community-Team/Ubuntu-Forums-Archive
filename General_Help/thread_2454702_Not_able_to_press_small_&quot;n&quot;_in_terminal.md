---
title: "Not able to press small &quot;n&quot; in terminal"
date: 2020-12-04
forum: General Help
---

### Post by akash-pandey on 2020-12-04
hello,
i am not able to press small n on terminal but able to press n everywhere else like browser and other application what should i do ?

---

### Post by Impavidus on 2020-12-04
Sounds like somehow a keyboard shortcut was defined for the terminal using the n key. The terminal than hijacks the n keystroke and performs some action, without passing it on to the application running in the terminal (like the shell).

Can you find anything about keyboard shortcuts in your (I assume) gnome-terminal? I use the xfce terminal myself, as I use Xubuntu.

---

### Post by Autodave on 2020-12-04
Is this a wireless keyboard?  If so, I had one with a similar problem.  It had worked for over a year and then the problem started.  I tried it on another machine and it did the same thing.  I had to replace it finally.

If it wireless, can you hook up a wired keyboard to see if you have the same issue?

---

### Post by CelticWarrior on 2020-12-04
@Autodave

Not an hardware (keyboard) issue because the OP is > [COLOR=#000000]not able to press small n on terminal but **able to press n everywhere else** like browser and other application[/COLOR]
And being the lowercase "n" only also rules out hardware.
And key failing can happen to any keyboard, why ask specifically about a wireless one?

---

### Post by HermanAB on 2020-12-05
I would first try a different terminal app, such as the good old xterm.  
If it has the same problem, look for a xmodmap configuration file in your home directory, maybe that is remapping the 'n'.  
Look in the usual Bash configuration files which may run when the terminal is started, such as described here [https://www.stefaanlippens.net/bashrc_and_others/](https://www.stefaanlippens.net/bashrc_and_others/)

---

### Post by deadflowr on 2020-12-05
Copy paste this into a terminal to see if 'n' it set as a shortcut
```
dconf dump /org/gnome/terminal/legacy/keybindings/
```
if it is, you can copy/paste this to reset to the defaults
```
dconf reset -f /org/gnome/terminal/legacy/keybindings/
```

---

### Post by akash-pandey on 2020-12-05
> **deadflowr said:**
> Copy paste this into a terminal to see if 'n' it set as a shortcut
```
dconf dump /org/gnome/terminal/legacy/keybindings/
```
if it is, you can copy/paste this to reset to the defaults
```
dconf reset -f /org/gnome/terminal/legacy/keybindings/
```


thank you so much.
it works

---

### Post by deadflowr on 2020-12-05
Good to hear.

For the record, Shortcuts can be set in the Preferences settings.
Should be accessible by clicking on the Terminal name in the top panel of the desktop.
Ubuntu has a mildly global menu setting for whatever app in is focus on the top panel.
(Mildly because some apps are more verbose than others, so I felt mildly fit well to describe it)

It should also be accessible by right clicking and selecting Preferences from a context window.

Unfortunately, The preferences settings don't ever seem to have any easy way to reset shortcuts,
only change them to another shortcut,
which is why I posted to the go-around of using the dconf backend, fwiw.

Ubuntu uses The GNOME desktop which uses dconf for the user's basic configuration system.
The terminal happens to be a GNOME app, so it luckily has a dconf setting.
More on dconf here: [https://wiki.gnome.org/Projects/dconf]("https://wiki.gnome.org/Projects/dconf")


If you feel the problem has been solved please mark this thread as solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by Autodave on 2020-12-05
I like to rule out hardware issues first.  If another keyboard was available, this would have taken less than a minute.  I have seen too many "wild goose" chases here and other places to not rule out the simple stuff.

From my own experience, I had a wireless keyboard that wouldn't do 3 capital letters only.

---

