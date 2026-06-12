---
title: "[SOLVED] CLI background goofy"
date: 2007-12-18
forum: General Help
---

### Post by evil316 on 2007-12-18
I'm using Gnome desktop with compiz-fusion enabled.  When I open my terminal I have it set to transparent background and the background it shows behind terminal is the desktop wallpaper despite the fact I have another app opened under it such as firefox.  Any ideas on how to fix this problem?

---

### Post by kaervos1024 on 2007-12-18
Setting the terminal background to transparent isn't processed through compiz-fusion. Its done through Gnome's facilities, and like transparent panels, all it does is draw your desktop background in there to make it *appear* transparent. What you can do to make it tasty is to turn off that "transparency", and instead just adjust the (true) alpha of your terminal window. This is done in compiz-fusion (if enabled) by holding ALT, and scrolling the mouse scroll-wheel.

Not exactly what you might be looking for as it will make the text more transparent as well, but its the only way I think you will get true compositing with other windows.

---

### Post by evil316 on 2007-12-18
It worked before.  I could have my terminal on top of firefox and see the firefox browser through the terminal.  Now it can be on top of firefox and it shows the desktop beneath.  I don't know what the problem was/is but I took your advice and now it's working like I want it to. 

Thanks!

---

### Post by imtheguru on 2007-12-18
> **kaervos1024 said:**
> Setting the terminal background to transparent isn't processed through compiz-fusion. Its done through Gnome's facilities, and like transparent panels, all it does is draw your desktop background in there to make it *appear* transparent.This is untrue. True alphatransparency is possible using just the terminal and without activating compiz transparency effects.

Will post screenshots in a few hours.

Cheers.

---

