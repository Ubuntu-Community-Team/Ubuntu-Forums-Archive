---
title: "compiz/emerald themes"
date: 2008-04-28
forum: General Help
---

### Post by Trmptxn on 2008-04-28
Hi everyone, 
I recently did a clean install of ubuntu 8.04 Hardy Heron.  It works awsome, i didn't have to do any configuration for my hardware (except for my wireless card but that worked after some fiddling =) ) I have an ati x1400 graphics card. 

The problem im having relates to themes, i cant figure out how to use the emerald theme manager to install .emerald themes that i get off of [http://www.gnome-look.org](http://www.gnome-look.org).  I highlight the theme and run emerald --replace, and the theme does come up, but the terminal box never gives me a prompt after that to input another command, it just kinda sits there and if i X out, all my window borders disapear until i use ctrl-alt-backspace to restart the session.  any help would be greatly apreciated =).

---

### Post by Zorael on 2008-04-28
The 'emerald --replace' command just invokes the window decorator itself, not the theme manager. Try running 'emerald-theme-manager' instead.

Add an ampersand (&) to the end of any terminal command to start it as a child process, making it run in the background. As far as I know, though, if you close the terminal window with the X button the child processes close, too. So you want to type **exit** instead.
```
$ emerald --replace &

$ exit     # safe way of closing the terminal
```

---

### Post by locketine on 2008-04-28
You should go into sysem->preferences->sessions and add "emerald --replace" as a startup program so you don't have to run that command every boot.

---

### Post by Trmptxn on 2008-04-28
awsome ^^ the comand worked and i am up and running, thanks! =)

---

### Post by adi_8079 on 2008-04-28
just what I was looking for! thanks!:)

---

