---
title: "What does &amp;&amp; do?"
date: 2007-12-26
forum: General Help
---

### Post by khughes on 2007-12-26
I have searched google for this but I can only find information on placing it in a command, I dont know exactly what it does. Anyone?

---

### Post by -grubby on 2007-12-26
it makes sure to run the command you enter after the && after the *first* command. For Example:
```
sudo apt-get install gnome-desktop && sudo apt-get remove gnome-games
```
first it would install gnome, then it would remove gnome-games (which install with gnome)

---

### Post by LaRoza on 2007-12-26
& runs an app in the background, so don't confuse them.

---

### Post by bodhi.zazen on 2007-12-26
command1 && command2

This runs command2 only after command1 completes without errors. If command1 exits with an error command2 will not run.

---

### Post by ~LoKe on 2007-12-26
```
cd /usr/share && ls
```
That command would enter you into the /usr/share directory then list it's contents.  It's a way of performing two or more commands in one line.

---

### Post by bodhi.zazen on 2007-12-26
> **~LoKe said:**
> ```
cd /usr/share && ls
```
That command would enter you into the /usr/share directory then list it's contents.  It's a way of performing two or more commands in one line.

Actually, ; is how you execute multiple commands.

so ....

```
cd /usr/share; ls
```

and if you want to list commands on multiple lines, for readability, use \ :

```
cd /usr/share;\
> ls
```


You get the ">" symbol in bash as a continuation of the previous line. Hit enter after the \ and the ls


&& is a conditional statement as above, try this :

```
cd /ussr/share && ls
```

The ls does not execute (unless you have a /ussr/share directory) because "cd /ussr/share" exits with an error.

---

