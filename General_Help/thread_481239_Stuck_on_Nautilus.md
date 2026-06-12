---
title: "Stuck on Nautilus"
date: 2007-06-22
forum: General Help
---

### Post by DMXell on 2007-06-22
Okay, so I'm fairly new to Ubuntu, but this is now the second time this has happened to me (first time I just decided to wipe Ubuntu and reinstall thinking it was a fluke). Whenever I boot into a certain user (my default one, but not root) the login message freezes on nautilus, but the wallpaper and junk load. I can't log out of the account (I use Control+Alt+Del to get out) and many programs won't work (see attachment for a screenshot). 

I think this is happening because of Beryl and Emerald Themer. Both times this happened I had installed them and updated them once I got the message to do so. I tried to remove Beryl  and had to do it via the terminal (I believe I was using the correct code, I'm new to the terminal: sudo apt-get remove beryl, which did confirm some sort of removal) but it made no difference, I got the same message. I even turned off all my my startup sessions just to make sure it was none of them.

Can anyone possibly help me? Thanks!

Oh yeah, if it makes any difference I'm on a Mac Mini with the intel processor, but I doubt it's actually the problem here, just thought I'd note it.

---

### Post by Qu4k3R on 2007-06-22
Are you using AIGLX ?
If you are, then try to login with the session: safe-gnome
Then open bery'ls properties (with right mouse click on the ruby's tray icon) then go to:
Advanced options>Rendering Platform> Force AIGLX

---

### Post by Crafty Kisses on 2007-06-22
> **DMXell said:**
> Okay, so I'm fairly new to Ubuntu, but this is now the second time this has happened to me (first time I just decided to wipe Ubuntu and reinstall thinking it was a fluke). Whenever I boot into a certain user (my default one, but not root) the login message freezes on nautilus, but the wallpaper and junk load. I can't log out of the account (I use Control+Alt+Del to get out) and many programs won't work (see attachment for a screenshot). 

I think this is happening because of Beryl and Emerald Themer. Both times this happened I had installed them and updated them once I got the message to do so. I tried to remove Beryl  and had to do it via the terminal (I believe I was using the correct code, I'm new to the terminal: sudo apt-get remove beryl, which did confirm some sort of removal) but it made no difference, I got the same message. I even turned off all my my startup sessions just to make sure it was none of them.

Can anyone possibly help me? Thanks!

Oh yeah, if it makes any difference I'm on a Mac Mini with the intel processor, but I doubt it's actually the problem here, just thought I'd note it.

Try booting in verbose mode, to see where it hiccups at.

---

### Post by DMXell on 2007-06-22
Qu4k3R: I did that but it didn't help. It seems like it's doing this before anything else activates since I also have Kiba Dock starting up with my computer, and it always starts before Beryl. I did notice that after 3 or so minutes it finishes booting so that I can log out though.

Codename: How do I boot into that mode?

---

### Post by Crafty Kisses on 2007-06-22
> **DMXell said:**
> Qu4k3R: I did that but it didn't help. It seems like it's doing this before anything else activates since I also have Kiba Dock starting up with my computer, and it always starts before Beryl. I did notice that after 3 or so minutes it finishes booting so that I can log out though.

Codename: How do I boot into that mode?

Reboot your computer completely and when it starts booting up press:
```
Ctrl+Alt+F1
```
It's pretty much a text-based login, but you can see what the error is, or where it stops.

---

### Post by DMXell on 2007-06-23
Okay, I did it but I am too new at this that I think I did something wrong. I entered my name and password, then it gave me some info on how everything in Ubuntu is free software and junk and then it gave me a normal terminal terminal prompt (dmxell@dmxell-desktop $ or whatever, like that). So I don't know what the problem is, but I think it involves Nautilus. The first time this happened I looked at some other threads about it and how others were having similar problems, but none of them really applied to mine as they simply got stuck with not even that little splash screen.

---

### Post by DMXell on 2007-06-24
Should I just reinstall Ubuntu again and simply not upgrade Beryl?

---

