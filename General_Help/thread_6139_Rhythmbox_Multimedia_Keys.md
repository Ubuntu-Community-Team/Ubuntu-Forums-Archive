---
title: "Rhythmbox Multimedia Keys"
date: 2004-11-25
forum: General Help
---

### Post by ken on 2004-11-25
Hi, I'm using Ubuntu 4.1 and I'm trying to get the settable keyboard shortcuts in Gnome to work with Rhythmbox.  Has anyone had any luck?

I've managed to map the volume control keys properly along with things like the web browser/mail keys etc.  But the play/pause, stop, prev, next keys don't want to work.

I'm wondering whether or not its my hardware (Gyration keyboard) or if it's something that I forgot to set within Gnome/Rhythmbox?

Ken

---

### Post by piedamaro on 2004-11-25
[QUOTE=ken]Hi, I'm using Ubuntu 4.1 and I'm trying to get the settable keyboard shortcuts in Gnome to work with Rhythmbox.  Has anyone had any luck?

I've managed to map the volume control keys properly along with things like the web browser/mail keys etc.  But the play/pause, stop, prev, next keys don't want to work.

I'm wondering whether or not its my hardware (Gyration keyboard) or if it's something that I forgot to set within Gnome/Rhythmbox?

Ken[/QUOTE]
 It' s something that _plain_ doesn't work in gnome. You need "acme" to use your multimedia keys.

---

### Post by ken on 2004-11-25
[QUOTE=piedamaro]It' s something that _plain_ doesn't work in gnome. You need "acme" to use your multimedia keys.[/QUOTE]
 Thanks, I'll give it a try when I get home... although I have to admit that it seems kinda strange.  I saw posts about v0.5 of Rhythmbox and requests for the multimedia keys to be incorporated into the next build.  I guess the authors didn't have enough time.

---

### Post by rune on 2004-11-29
[QUOTE=piedamaro]It' s something that _plain_ doesn't work in gnome. You need "acme" to use your multimedia keys.[/QUOTE]
That's is just wrong!

Acme has been put into gnome from 2.6 and we're at 2.8 now. 

I've been fairly succesfull at getting rhytmbox working with my Labtec keyboard.
[QUOTE=ken] I'm wondering whether or not its my hardware (Gyration keyboard) or if it's something that I forgot to set within Gnome/Rhythmbox?[/QUOTE]
When setting the shortcuts with Computer > Desktop Preferences > Keyboard Shortcuts ; do you get a response with those buttons, like a XF86Next or 0x99? Try mapping the prev and next buttons with something that does work like email.

---

### Post by GeneticFreek on 2004-12-01
Hey there,
my buttons bring up a response in the Keyboard Shortcuts window, and the volume buttons work, but the play/next/last/stop buttons don't control rhythmbox.

---

### Post by scoon on 2004-12-01
Hey there, 

Check out the man page for xev.  That is how keys values get mapped to their X names. 


scoon

---

### Post by piedamaro on 2005-01-23
I've written a little howto here: [http://www.ubuntuforums.org/showthread.php?t=12159](http://www.ubuntuforums.org/showthread.php?t=12159)

---

