---
title: "gnome screensaver always asks for password"
date: 2007-06-18
forum: General Help
---

### Post by tvst on 2007-06-18
This is pretty strange and has happened to me since edgy on two very different computers, but I haven't been able to find anyone with the same problem online: when resuming from the screensaver I always get prompted for my password. I don't know why, since the "lock screen when screensaver is active" checkbox is unchecked.

I know that not having a password for resuming from your screensaver is a security risk, but i'd like to change this behavior on my home machine (If someone has unattended access to my home I have bigger problems to deal with!)

---

### Post by jimrz on 2007-06-18
> **tvst said:**
> This is pretty strange and has happened to me since edgy on two very different computers, but I haven't been able to find anyone with the same problem online: when resuming from the screensaver I always get prompted for my password. I don't know why, since the "lock screen when screensaver is active" checkbox is unchecked.

I know that not having a password for resuming from your screensaver is a security risk, but i'd like to change this behavior on my home machine (If someone has unattended access to my home I have bigger problems to deal with!)

from the panel go to System > Preferences > Screen saver and see if the "lock screen when screen saver is active" box is checked. if so, uncheck it. if not, you might try checking it and then closing the window then go back and uncheck it

---

### Post by tvst on 2007-06-20
i had tried that already but, just for good measure, decided to give it another go. still doesn't work. any other ideas?

---

### Post by nikopol on 2007-06-20
This solved my problem 
[http://ubuntuforums.org/showthread.php?t=201256](http://ubuntuforums.org/showthread.php?t=201256)

---

### Post by tvst on 2007-06-21
that works! i did it slight different from the solution posted there, though, just to see if it would still work. i opened gconf-editor, navigated to /apps/gnome-power-manager/ then unchecked 'lock_on_blank_screen' and checked 'lock_use_screensaver_settings'. so now the screen locking follows the behavior set in the screensaver gui. i think this should be the default settings, so i'm going to post a launchpad entry on it.

thanks for your help

---

