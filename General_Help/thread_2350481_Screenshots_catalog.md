---
title: "Screenshots catalog"
date: 2017-01-24
forum: General Help
---

### Post by miniKOX on 2017-01-24
Hello.

My problem is, that when I push Printscreen button on my keyboard, the gnome-screen shoot application saves it by default to Pictures directory.

I want this program to **ask me** where to save every single screenshot that I have made - how to do this?

---

### Post by vasa1 on 2017-01-24
> **miniKOX said:**
> Hello.

My problem is, that when I push Printscreen button on my keyboard, the gnome-screen shoot application saves it by default to Pictures directory.

I want this program to **ask me** where to save every single screenshot that I have made - how to do this?

The *man* page for *gnome-screenshot* has this:```
       -i, --interactive
              Interactively set options in a dialog.

```
So, if you run```
gnome-screenshot -i
```you'll get a succession of two windows. The first lets you choose whether you want to capture the whole screen, the active window or a selected area. The subsequent window allows you to select both a filename *and* a destination. See the attached image. This is with the version of gnome-screenshot for 16.04. Older or newer versions may be different.

---

### Post by miniKOX on 2017-01-25
Thank You, but my problem is, that I want - whenever I push PrtScr key on keyboard to run this program, and NOT to save image into my Picture directory(which is currently happening).

I want this program to always ask me, where to save screenshots - now it is just saving them to Pictures catalog.

---

### Post by vasa1 on 2017-01-25
> **miniKOX said:**
> ... whenever I push PrtScr key on keyboard to run this program, and NOT to save image into my Picture directory(which is currently happening).
...

I don't know which distro you're using but I'm guessing you need to alter what happens when PrntScrn is pressed. On your system, that key is bound to an action involving gnome-screenshot. You need to find out what that action is and change it to what I mentioned earlier: *gnome-screenshot -i* (or *gnome-screenshot --interactive*).

Before doing so, you can verify that *gnome-screenshot -i* does what you want by running it in a terminal.

---

