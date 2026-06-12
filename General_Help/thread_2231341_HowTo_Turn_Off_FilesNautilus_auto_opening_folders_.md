---
title: "HowTo: Turn Off Files/Nautilus auto opening folders during drag and drop"
date: 2014-06-25
forum: General Help
---

### Post by agrayray on 2014-06-25
I use drag and drop to move folders around quite a lot and the feature of the new files that is auto opening/going to folders that it thinks the mouse hovers over is driving me nuts..too many times it opens folders that "are in the way" of moving to the folder I want..in the end..I have to spend so much more extra time backing out of directories..searching for folders where things are mistakenly moved to etc..

Is there a way to turn off this behavior and force me to select the folder I want and right click to paste or double click to enter it...ie..the old way?

THANKS MUCH!

---

### Post by Jonor on 2014-06-25
Sounds like a bug or hardware, try rebooting with a different mouse.
What OS is it, e.g. Ubuntu Gnome 14.04 ?

---

### Post by mc4man on 2014-06-25
It can only be turned off in the source, then rebuilt, there is no user config here
auto open dir.  on hover can occur in 4 areas - 
icon view (in nautilus window
sidebar
breadcrumbs
listview

I find the onerous one to be in icon view (canvas view), the other 3 are semi useful. So to that end wrote a patch to revert, if interested in building the nautilus source can attach it.

---

### Post by agrayray on 2014-06-26
Yes, it is the icon view that is the real issue, and occurs Ubuntu 14.04, Files w Unity.  I have no external mouse, not plan to use one, but instead use mousepad/trackpads only..thanks for the info, sad that its not an option to configure natively..appreciate  it!

---

