---
title: "How do I run a program from the terminal?"
date: 2006-10-24
forum: General Help
---

### Post by lotharamious on 2006-10-24
I was wondering how you install a program so that you can type in a single word in the terminal and get it to run.  So, I guess I'm wondering where I would install the files, then how do I make the executable script(?) to run the program.  I'm trying to do this with stepmania.  







Kubuntu Dapper 6.06.1
KDE 3.5.5

---

### Post by pgatrick on 2006-10-24
If you already have the program, then it just needs to be in your path to execute from anywhere. /usr/local/bin should work, or you can alternately add new directories to your path. Oh, and to make it executable, just use chmod to change the permissions, 'chmod +x (file)' should work afaik.

---

### Post by ~LoKe on 2006-10-24
Depends on what you install.  If you know the name...it could be as simple as...

```
sudo apt-get install firefox
```
That would, obviously, install firefox. Then, to run it...
```
firefox
```
However, if you want to continue having access to the terminal while firefox is running, you should have a trailing ampersand.
```
firefox &
```

---

