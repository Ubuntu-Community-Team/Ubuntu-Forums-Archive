---
title: "gnome-terminal stuck on start"
date: 2013-01-29
forum: General Help
---

### Post by nadavvin on 2013-01-29
[[img]http://s2.postimage.org/9rp4m0lcl/gnome_terminal.jpg[/img]](http://postimage.org/image/9rp4m0lcl/)

Thank for your help

ubuntu 12.10

---

### Post by Habitual on 2013-01-30
What's the question? :confused:

---

### Post by kanikilu on 2013-01-30
It looks like you have a cursor - what happens if you just type a command like ls and press enter? Does anything come up?

If so, maybe somehow your gnome-terminal profile preferences got changed to have the text the same color as the background?

If that's the case, when gnome-terminal is up, go up to the menu bar at the top of the screen (not the top of the terminal window) and see if you can access the profile preferences under the Edit menu. Then check the Colors and Background tabs and make sure you have different/contrasting colors for the text and the background...

---

### Post by nadavvin on 2013-01-30
No! It's stuck!

The menu not open.

after some second a pop up appear that ask if to wait or kill it...

---

### Post by kanikilu on 2013-01-30
Ok - have you tried removing it and re-adding it from the Software Center?

Another option is to install another terminal - something like ROXTerm, XTerm, rxvt, etc. I know that's only working around the problem, not fixing it. But, from there maybe you can diagnose the gnome-terminal problem. For instance, from another terminal emulator, run gnome-terminal and see if you get any useful output or error messages in the console...

---

