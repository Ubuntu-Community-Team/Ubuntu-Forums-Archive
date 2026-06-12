---
title: "How do you &quot;save&quot; the DISABLED_MODULES= fix?"
date: 2007-05-01
forum: General Help
---

### Post by Jonathan123 on 2007-05-01
So once you open up the linux restricted modules and edited it, how do you save it and exit?

I enetered it, but how do I save it?

---

### Post by Jonathan123 on 2007-05-01
I think I found the answer.

I read you hit Ctrl-o

However, when I do, it just puts the marker at the top of the window, but I'm not sure if it's "saved" or not.

---

### Post by jocko on 2007-05-01
From your problem I guess that you are trying to use vi to edit the file?
I don't know how to save things in vi, but you could try another editor.
If you have a working graphical environment you could use gedit (or kate if you use kde):
```
sudo gedit /etc/default/linux-restricted-modules-common
```
If you are stuck in a terminal you could try nano (save with ctrl+O, exit with ctrl+X):
```
sudo nano /etc/default/linux-restricted-modules-common
```

---

### Post by jimbob on 2007-05-01
If you are in vi or vim hit esc to make sure you are out of insert mode and then shift-colon should put a colon at the bottom left of the screen.
At the colon enter wq which will write the file you have changed and exit vi (vim).
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

