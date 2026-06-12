---
title: "Stray Pixels?"
date: 2005-03-24
forum: General Help
---

### Post by eudemon on 2005-03-24
Hello everyone!  I recently installed Hoary 64-bit on my amd64 laptop, and this is my first post to your forums.  You really have a great community here.  Between the nicely detailed how-tos, and the old forum posts, I (a complete linux n00b) was able to accomplish everything that I wanted to with virtually no problem.

So everything works great, except for one minor annoyance; after being logged in for a while, stray pixels will appear in the gui.  Once there, the only way to eliminate them is to restart the desktop, and they continue to get worse until you do so.  They also leave trails inside windows when scrolling or moving.  It seems to be triggered by resizing a window; I can force it to occur almost immeadiately by resizing a window quickly and repeatedly.

I have a radeon 9600 mobility, and have installed fglrx and set xorg.conf to use it as the driver.  The pixels still appear though.  Anyone have an idea to prevent this?

---

### Post by alastair on 2005-03-24
Have you tried the open source driver (radeon)?
Worth seeing if this is an ATI driver issue.

The other thing you could try, to get rid of them, is to switch to a text VT and then back to X - see if this clears them with no need to logout i.e. CTRL+ALT+F1 then CTRL+ALT+F7.

---

### Post by eudemon on 2005-03-24
[QUOTE=alastair]Have you tried the open source driver (radeon)?
Worth seeing if this is an ATI driver issue.

The other thing you could try, to get rid of them, is to switch to a text VT and then back to X - see if this clears them with no need to logout i.e. CTRL+ALT+F1 then CTRL+ALT+F7.[/QUOTE]
 Switching to a text VT and back clears the trails left from scrolling, but not the pixels themselves.  The same happens whenever a window refeshed by switching workspaces or minimizing and restoring the window.

Trying out the radeon driver now.

---

### Post by eudemon on 2005-03-24
Nope, they still show when the driver is set to radeon.  :???:

---

### Post by eudemon on 2005-03-31
Okay, I think I've fixed the pixel corruption.  Added the line: 

Option "mtrr" "off" 

to the device section of xorg.conf, and haven't seen the error repeat since.  :)

---

