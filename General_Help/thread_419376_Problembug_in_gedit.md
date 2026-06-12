---
title: "Problem/bug in gedit?"
date: 2007-04-22
forum: General Help
---

### Post by ardchoille42 on 2007-04-22
I am using gedit 2.18.1 in the Window Maker window manager on Ubuntu 7.04 (Feisty Fawn) and there is a problem with gedit.
Steps to reproduce the problem:
       
1. open gedit
2. Click on File -> Save As
3. Click the arrow next to "Browse for other folders" to expand the folder area of the dialog
4. Click that arrow again to shrink that dialog
5. What happens?

What I am seeing is the Save As dialog continually expanding and shrinking (animation?) to the right making it difficult to click the Cancel button. Clicking the title bar of the Save As dialog stops the animation momentarily but continues when you release the mouse button.

Is this a known bug?

**EDIT:** I am seeing that this problem is with the GTK2 open/save as dialog in all GTK2 apps, not just gedit. And, I don't use the gnome desktop environment.


This bug has been filed: [https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/105265](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/105265)

I added more information to the bug report that I felt would help the trouble shooters.

---

