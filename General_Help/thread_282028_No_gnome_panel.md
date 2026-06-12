---
title: "No gnome panel"
date: 2006-10-22
forum: General Help
---

### Post by kornhead127 on 2006-10-22
I ran into a bit of a problem. I can't remember exactly how my panel got fubared, but I was trying to install some new gnome stuff in Synaptic and after I installed something. I really can't remember what it was, but my panel 'unexpectedly quit' and everything I tried has done nothing. Any help? ](*,)

---

### Post by skwillz on 2006-10-22
If you don't have any panels, then I assume it's probably difficult for you to actually go into anything?

If you can find your way into an application launcher or the terminal, run "gnome-panel".

---

### Post by kornhead127 on 2006-10-22
Yeah that was my first instinct but the terminal won't open! I right click on my desktop and selct open terminal but nothing. I did figure out how to get synaptic to open when my session starts so is there an alternate terminal I can install?

---

### Post by skwillz on 2006-10-22
How about right click desktop, create launcher?

And from there, either launch gnome-terminal to launch the panel, or just try to launch gnome-panel.

---

### Post by kornhead127 on 2006-10-22
nope nothing I tried that too. I can only create folders with I found was the only way to launch nautilus.

---

### Post by skwillz on 2006-10-22
Alright.. at least we know what you can do now.

So if you can get into Nautilus, then you can probably make a file right?

What about making a script to launch the panel?

#!/bin/bash
gnome-panel

Give it a name like "panel.sh" and set the permissions to allow owner execution.

I don't know if this would work since I figure it does the same exact thing as the options mentioned before.

---

### Post by kornhead127 on 2006-10-22
O, I didn't think of that. I'll give it a try. I'm on my WinD0ze box right now. Gimme a minute.

---

### Post by skwillz on 2006-10-22
Oh sorry I just noticed that you use Xubuntu...

In that case, I don't think any of these commands would work.

---

### Post by kornhead127 on 2006-10-22
Oh no don't worry about that.
I'm using BeatriX based off of ubuntu.

---

### Post by kornhead127 on 2006-10-22
Damn, it won't open. I get nothing, I guess cuz my terminal wont open?

---

### Post by skwillz on 2006-10-22
I suppose you could try restarting the X server, although I doubt this would help any.

I think CTRL+SHIFT+BACKSPACE will exit out of X.

Then at the commandline, type startx to get back into X.

---

### Post by kornhead127 on 2006-10-22
I've been doing this repeatedly to switch between my user and root. I also tried useing [ctrl]+[alt]+F1 to use "rm -fr ~/.gnome ~/.gnome2" hopefully to delete user settings and restore defaults? Did I **** up? But that wouldn't explain why a terminal wont open.

---

### Post by kornhead127 on 2006-10-22
I'm gonna try booting in single user mode from grub. I don't know what that will acheive but maybe I can fix something.

---

### Post by kornhead127 on 2006-10-22
I'm currently in single user mode running aptitude and upgrading everything I can. hopefully this will fix my problem.

---

### Post by kornhead127 on 2006-10-22
I tried every trick in the book and finally I solved my problem thanx for any help at all. :KS  :-D

---

### Post by graigsmith on 2006-10-22
try ctrl - alt - f1  and see if you can run it from that terminal.

---

### Post by ser1alsn1per on 2006-10-22
try alt f2 to run programs

---

