---
title: "Change Screensaver w/o Opening Setting"
date: 2008-03-28
forum: General Help
---

### Post by dr.silly on 2008-03-28
I have a OpenGL screensaver which crashes my computer. The preview also crashes my computer. So, I need a way to change the screensaver back to black screen without opening up the settings dialog.

(or just disable screensaver)

---

### Post by dr.silly on 2008-03-28
I already have drivers installed; compiz works fine.

---

### Post by Tux Aubrey on 2008-03-29
This is a bump

I have exactly the same problem with the default Gnome "Braid" screensaver in 7.10.  I've had an ongoing problem whenever "Braid" activates as one of the random screensavers.  It freezes the display.  I can usually restart X (Ctrl-Alt-Bksp) after it activates but I selected it in the screensaver preferences GUI and now that has crashed and I can't get out of it and have no keyboard or mouse functions at all.

I am running compiz-fusion and have a nvidia card.

I think I need to access the screensaver controls from the command line and, if possible, delete "Braid"

---

### Post by Tux Aubrey on 2008-03-29
[SOLVED] - for me anyway.  I hope this also helps dr. silly

The answer is to open gconf-editor from the command line, navigate to apps>gnome-screensaver and change the mode (dbl click) back to random.  You can then quit and use the gui to select a particular (functional) screeny or turn it off altogether.

Here's the gconf-editor window with the relevant bits highlighted:

[IMG]http://ubuntuforums.org/g/images/167727/1_Screenshot-Configuration_Editor_-_gnome-screensaver.png[/IMG]

---

