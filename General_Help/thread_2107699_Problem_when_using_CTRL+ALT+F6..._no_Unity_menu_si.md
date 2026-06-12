---
title: "Problem when using CTRL+ALT+F6... no Unity menu sidebar..."
date: 2013-01-22
forum: General Help
---

### Post by KingNeil on 2013-01-22
I am on Ubuntu 12.04.

Here is what I do...

(1) I use CTRL+ALT+F6 to switch to another screen
(2) It goes to command prompt, so I use **startx -- :1** to start a new graphical environment.
(3) It loads fine, but only has the desktop... as in, there is no sidebar with the menu items, and therefore, I can't start any programs, or do anything useful at all.

So... is there any way I can get the Unity sidebar to show up... or is it possible that there is a RAM/computer component deficit on my hardware... or something else?

Like.. is there some command I can issue, prior to startx (seeing as I can't do anything once I get there), in order to make sure the Unity sidebar shows up...?

Thanks

---

### Post by KingNeil on 2013-01-22
OK. Don't worry. I solved it myself.

I created an empty text file, using right-click on the desktop > Create New Document

And then I entered the following into the file

**unity**

And then I right-clicked the file, and changed it to an executable file, and then double-clicked, clicked Run, and it started unity, and now I have my sidebar.

I just typed this out in case anyone has the same problem in the future.. Frankly, I'm running this off a live disc CD, and so, it seems to be running low on RAM, and that's why it didn't initially start up.

---

### Post by marin123 on 2013-01-22
Actually it is Ctrl+Alt+F7.

Have you tried that?

---

### Post by CaptainMark on 2013-01-22
I'm assuming the op wants a second x server,

---

