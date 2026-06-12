---
title: "Move window to right side of screen with a keystroke"
date: 2022-08-28
forum: General Help
---

### Post by Paddy Landau on 2022-08-28
I want to move a window to the far right-hand side of the screen with a single keystroke.

On Ubuntu 20.04, I had a script that ran this command:
```
xdotool getactivewindow windowmove 100% y
```
I assigned this script to a keyboard shortcut, and it worked perfectly.

On Ubuntu 22.04, this doesn't work properly. It sends the window so far to the right that only small bit is visible. The attached screenshot shows the right side of my screen with the terminal just showing at the edge.

Note: I am logging into X.Org, not Wayland.

Is there a simple and straightforward solution to this, or do I need to have my script calculate window and screen sizes?

Thank you

---

### Post by tea for one on 2022-08-28
Do you mean Tile Windows?
Super + Right Arrow (or Left Arrow)
Although two keys needed?

---

### Post by Paddy Landau on 2022-08-28
> **tea for one said:**
> Do you mean Tile Windows?..
Thanks, I'm aware of that one. Unfortunately, that tiles the window, which resizes it. I want the window's size to remain unchanged.

I'll have to do a little programming in my script to calculate screen and windows sizes. It's a shame that the 100% option no longer works!

---

### Post by tea for one on 2022-08-28
> **Paddy Landau said:**
>  I want the window's size to remain unchanged.
Ah, I see the conundrum.
There is an extension, which mentions:-
> Gnome-shell extension that improves window tiling capabilities of stock gnome-shell.
gTile is used to moves/resize windows on a configurable grid scheme.
It can be used with either the mouse, or keyboard, including customizable keyboard presets for immediate window placement.
[https://github.com/gTile/gTile](https://github.com/gTile/gTile)
Worth a look?

---

### Post by norobro on 2022-08-28
That command works on my 22.04 box from the command line moving a terminal window. 

Is the Xserver correctly recognizing your monitor size?```
xwininfo -root
```

---

### Post by Paddy Landau on 2022-08-28
> **tea for one said:**
> [https://github.com/gTile/gTile](https://github.com/gTile/gTile)…
Close, but unfortunately not quite!
> **norobro said:**
> Is the Xserver correctly recognizing your monitor size?```
xwininfo -root
```
Yes, as does wmctrl.

But, bizarrely, it's suddenly working correctly! I cannot say why. What has changed? Who knows! This will go down as one of the mysteries of computer gremlins.

So, I'm marking this thread as solved. Thank you for the time you've spent.

---

