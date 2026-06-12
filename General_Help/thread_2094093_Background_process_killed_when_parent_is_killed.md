---
title: "Background process killed when parent is killed"
date: 2012-12-12
forum: General Help
---

### Post by kuifje09 on 2012-12-12
When[I] I start a window (X) then start i.e. xclock &  ( to get it in de background )
The clock starts, but as soon I kill the parent window ( press X )  the clock is killed too.
When I kill the window with CTRL-D  the clock remain on my desk.

Is this normal behavior? I doubt.

Running ubuntu 11.04  , sometimes Gnome, sometimes XFCE.
[/I]

---

### Post by evilsoup on 2012-12-12
You mean a terminal emulator? The window that pops up when you press 'ctrl+alt+t'? What you are describing is the standard behaviour, when you close a terminal emulator, any processes it is running end.

In your particular case, I'd recommend using 'alt+f2', which will bring up a program launcher. You can input any terminal command and it will be run; in your case 'xclock'.

---

### Post by kuifje09 on 2012-12-14
Hi, and thanks. 

What me surprised was the background job is killed when the terminalemulator is killed.
The terminal emulator is foreground and the as example xclock is background.
I expected it to remain running when the terminalwindow was killed. ( X )
When you just stop it ( ctrl-D ),  the xclock keeps on running.
I remember, when working on HP-UX , I had all background processes ( started from this window ) to kill by hand when the terminal was killed.

---

