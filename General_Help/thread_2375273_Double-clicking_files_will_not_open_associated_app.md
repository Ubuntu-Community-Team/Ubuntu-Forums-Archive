---
title: "Double-clicking files will not open associated applications"
date: 2017-10-23
forum: General Help
---

### Post by ncweber on 2017-10-23
After upgrading to 17.10, I cannot open files from Nautilus by double-clicking them.  The system shows the "busy" mouse pointer for a few seconds, but then nothing happens.

I can open files by right-clicking the file in Nautilus, clicking Select other application (selecting the default directly does not work), and then selecting the default application from the other applications list.

Anyone else experiencing this issue?

---

### Post by ajgreeny on 2017-10-23
What does a **right click ->Properties** show as the default application to open the file(s)?

Is it the same for all file types, or just one, or a few?

---

### Post by ncweber on 2017-10-29
> **ajgreeny said:**
> What does a **right click ->Properties** show as the default application to open the file(s)?

Is it the same for all file types, or just one, or a few?

So, right-click > Properties shows that each type of file has the correct default program assigned.  The issue affects all files no matter what type they are.  I've also discovered that this happens whether I login with Wayland, or X.Org, so it appears to be a Nautilus issue?

---

### Post by rcstark on 2017-11-10
I have the same problem with the behavior as noted by ncweber. I found that if I open a folder as root, the double-click function works (i.e. files open with the designated default application). How can I get it to work without root privileges?

---

### Post by ncweber on 2017-11-15
Okay, so, apparently a recent update resolved this issue, but I'll be darned if I know which one.  Possibly the Gnome Desktop Settings updates.

---

### Post by apos on 2017-11-25
Hi,

did anyone find a solution?
On one of my PC's updating from 17.04 to 17.10 the problem occures, on the other not.

I already tried to move ~/.config/nautilus and ~/.gconf/nautilus
But this did not succeed.

Greets Axel

---

### Post by apos on 2017-11-26
Hi, 

I could **solve the problem**: playing around with xdg-open lead me the path.
"xdg-open file.ext" always leads to open a file with nautilus per default. This loops and loops, so the app get never really started. 

The problem was an old xfce installation and the **package "exo-utils".**
Remove "exo-utils". This is an well known and older problem:

```
sudo apt-get remove --purge exo-utils
```

And everything worked as expected.

Further reading:

* 2014: [https://unix.stackexchange.com/questions/157355/xdg-open-just-opens-nautilus](https://unix.stackexchange.com/questions/157355/xdg-open-just-opens-nautilus)
* 2011: [https://bbs.archlinux.org/viewtopic.php?id=113908](https://bbs.archlinux.org/viewtopic.php?id=113908)

Cheers 
Axel

---

