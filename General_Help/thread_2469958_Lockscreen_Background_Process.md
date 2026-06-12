---
title: "Lockscreen Background Process?"
date: 2021-12-15
forum: General Help
---

### Post by sidecarrig on 2021-12-15
Hi,
I have a Bash script running in the background daily. *When the screen locks is there a process name that my script can ‘ps -ef | grep …’ for to see if my workstation is locked?* (BTW, it’s an ancient .csh reminder facility that I’m rewriting in bash that’s very much like ‘at’ but will give the user the option of what happens when the workstation/screen is locked. The easiest example is: Don’t play the audio alert message when the screen is locked.)
TIA

---

### Post by CatKiller on 2021-12-15
I expect that there'll be some kind of dbus signal you can read to determine whether the screen is locked, but it's not something I've particularly looked at.

---

### Post by sidecarrig on 2021-12-15
Thanks. I was *really* hoping to avoid dbus and go with the simple ps | grep. But if I must, I must!

---

### Post by Holger_Gehrke on 2021-12-15
It kind of depends on the screen saver/locker you're using. light-locker has a command line tool 'light-locker-command' which will give you the current state if you call it with the option '--query'. xscreensaver has xscreensaver-command, but no '--query' option. Instead it has '-watch' which will keep on running until you stop it and print the currrent state of the locker/screen saver whenever it changes.

Holger

---

### Post by sidecarrig on 2021-12-16
Thanks Holger

---

