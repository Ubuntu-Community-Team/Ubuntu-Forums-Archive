---
title: "[SOLVED] Stupid experiment... now, fonts possibly broken"
date: 2007-07-24
forum: General Help
---

### Post by nvteighen on 2007-07-24
OK, this may be really strange; if no one replies, I'll assume I'm just wrong and it's my imagination. Here's my story:

I wanted to try KDE, so I install it with aptitude, play around with it and didn't like it. No, KDE is not for me... just don't know why. So, I removed it with aptitude... Then, I tried Xfce... I like it but prefer GNOME, so I removed it too.

Ok, back into GNOME, I realise that fonts look different in Terminal and in Firefox. I revised if I had left any font library from KDE or Xfce and found nothing... But I'm pretty sure they're different; or is it just an ilussion caused by quick desktop environments changes? (what I mean: if there's a possibility that I've broken something?)

Or is it a punishement for making silly experiments??

Thanks!

---

### Post by nvteighen on 2007-07-24
Update: I'm not the only one having this problem. Look at [this message]("http://ubuntuforums.org/showthread.php?t=498402").

The problems seems to be related with the ttf-dejavu package (Monospace, Sans Serif, and similar fonts).

---

### Post by mannheim on 2007-07-24
One horrible thing that KDE does, under some circumstances, is create a file in your home directory called .gtkrc-2.0 which sets some defaults for fonts and styles in gtk applications. If this file is created, it will override your gnome preferences for things like menu fonts and such-like when you return to gnome.

It's worth checking if this is the problem. If there's a file called .gtkrc-2.0, rename it to something else and then logout and login.

---

### Post by nvteighen on 2007-07-25
No way. There is a file called .gtkrc-2.0, but it was created by me. I deleted one called .gtkrc-2.0-kde, and restarted X, but it still doesn't work.

The affected apps seem to be firefox & gnome-terminal. Nothing else, at least for now. I'm considering to reinstall the ubuntu-desktop package and see if it restores GNOME.

---

### Post by nvteighen on 2007-07-25
Solved reinstalling Ubuntu.

---

