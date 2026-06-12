---
title: "[SOLVED] Google Earth and Hardy"
date: 2008-05-18
forum: General Help
---

### Post by kvolden on 2008-05-18
Hi! First of all, excuse my noobness. I just installed Google Earth through Synaptic, but it doesn't quite work as it should. The main "box", as in the place in the Google Earth window that shows the earth and its details, is completely black unless I move the mouse cursor around in the picture. If I move it, everything works, but it's quite annoying.
Running glxinfo shows "direct rendering: Yes", and glxgears runs with some amounts of flickering, with ~2300 fps. I have an ATI Mobility Radeon X1300 card, with drivers installed throuh EnvyNG, running on Hardy.
Any help appreciated!

---

### Post by angry_johnnie on 2008-05-18
Are you using compiz?  That happens sometimes... lots of times :-) with compiz and google earth.  You would have to disable compiz while using google earth.  I guess the easiest, fastest way to do it would be to install fusion-icon.  You can either get it from synaptic (system > administration > synaptic), or by opening a terminal and typing:

```
sudo apt-get install fusion-icon
```

It will be available in Applications > System Tools > Fusion icon

Launching it will put an icon in your system tray, where you can quickly change back and forth between compiz and metacity.

---

### Post by kvolden on 2008-05-18
Great! It works! :-D Even glxgears stopped flickering. Is this anything Compiz will be fixing any time soon, you think?

---

### Post by igorlunamoura on 2008-07-29
It doesn't sound like a solved problem. It's a short term solution that must be improved. Sorry if i am wrong and it is Compiz's or Google's problem. 

Just for record the difference between applying this method in instead of turning on and off the special effects in the Appearance tab is that, using the former, compiz settings (like the Cube) are mantained.

---

