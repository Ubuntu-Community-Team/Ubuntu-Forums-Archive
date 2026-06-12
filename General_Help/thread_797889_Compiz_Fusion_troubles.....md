---
title: "Compiz Fusion troubles...."
date: 2008-05-17
forum: General Help
---

### Post by Slacker.ksg5 on 2008-05-17
Well I accidently set it to all windows 100% transparent. Long story short I can't see anything including the gnome panels. 

I tried the following with no Luck:

I tried reinstalling the compiz packages through synaptic.
I tired
sudo apt-get remove compiz
I also tried making the xserver-xgl with the disable document in the home directory.
I also tried deleting the files under ~/.compiz and that didn't work either... is there a way that I can restore default compiz settings?

Thanks in advance.

---

### Post by kawaji on 2008-05-18
Have you already checked ~/.gconf/apps/compiz, if you are using gconf-backend for compiz ?

---

