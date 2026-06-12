---
title: "Root"
date: 2007-04-21
forum: General Help
---

### Post by Reichicken on 2007-04-21
I need to know how to get into root, so I can get my mouse to work.... I was told CTRL+ALT+F1, but when I do that, and type root it asks for a password... My password for my user doesnt work, what am I doing wrong?

---

### Post by madmetal on 2007-04-21
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Reichicken on 2007-04-21
Ok, new issue...

People tell me to go into sudo, and I do...


They say use this command... Sudo /etc/x11/xorg.conf

It says that isnt a command.

---

### Post by madmetal on 2007-04-21
> **Reichicken said:**
> Ok, new issue...

People tell me to go into sudo, and I do...


They say use this command... Sudo /etc/x11/xorg.conf

It says that isnt a command.

sudo gedit /etc/x11/xorg.conf

in order to modify the file..

---

### Post by Reichicken on 2007-04-21
Gives a GTK warning, and cannot display it.
D:

---

### Post by RedSquirrel on 2007-04-21
Try:

```
gksudo gedit /etc/X11/xorg.conf
```

It's better to use gksudo for graphical applications. Note as well that the directory is named X11, not x11 (the X is uppercase).

---

### Post by shinythings on 2007-04-21
If you are not in the graphical environment you could use nano:

```
sudo nano /etc/x11/xorg.conf
```

If you open a terminal in GNOME (Applications > Accessories > Terminal) you can use gedit (which you might find to be more intuitive):

```
gksudo gedit /etc/x11/xorg.conf
```

---

### Post by Reichicken on 2007-04-21
I have GNU nano open (I assume that is what I should be in)

But there is nothing in there about Input device or mouse...


EDIT: Didnt read squirrels post, I solved the issue. I will tell how it goes. Thanks all!

---

### Post by Reichicken on 2007-04-21
Ok, I changed the protocol from" ImPS/2" to "PS/2" should I put it as USB? Also, how do I exit and save the file?

---

### Post by RedSquirrel on 2007-04-21
gedit:

To save the file, you can go File -> Save, or you can press Ctrl-s.

To exit, go File -> Exit (or it might be Quit; I haven't used gedit in a while), or press Ctrl-w.


nano:

Press Ctrl-x. It will ask you if you want to save. Say 'y' and press ENTER.


I have my mouse on PS/2, and I'm afraid I can't recall the settings for USB. Sorry.

---

### Post by Reichicken on 2007-04-21
One problem after another....

Now my X server wont work.

---

