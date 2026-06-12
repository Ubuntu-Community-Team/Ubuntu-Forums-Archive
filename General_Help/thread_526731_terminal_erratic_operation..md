---
title: "terminal erratic operation."
date: 2007-08-15
forum: General Help
---

### Post by mimsmall on 2007-08-15
My ubuntu 6.04 has been working fine, until today, that is.
I opened a terminal and attempted to cd to another directory and get this error: no such file or directory. So, I tried several other folders with the same result. So I attempted to open my web browser with sudo seamonkey and was asked for the password as always and I entered it and the error was wrong password. Next I went to the administrative menu to check on groups and users and couldn't get in because the password wasn't recognized.

I have been using my machine daily for several years, can some one point me at the solution?

---

### Post by kevinlyfellow on 2007-08-15
thats weird, are you using gnome-terminal?  Does the same issue occur when your in tty1 (ctrl-alt-f1)?

Maybe you just need to resest the settings for gnome-terminal? 
```
rm -r ~/.gconf/apps/gnome-terminal
```

---

### Post by mimsmall on 2007-08-16
Maybe I just need to get my head out. The last change I made before the trouble started was plug in CueCat. When I came to my senses, I unplugged it and all is well.

---

