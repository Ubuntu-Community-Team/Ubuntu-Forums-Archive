---
title: "cursor freezes when keyboard used"
date: 2007-11-10
forum: General Help
---

### Post by battles33 on 2007-11-10
when i hit a key on the keyboard, the cursor freezes on screen. for example, when scrolling with the mouse from one side of the screen to the other, the cursor will freeze for a moment when i hit a key on the keyboard and then after that moment it will appear where it should be (so it's as if the keyboard causes the display of the cursor position to be frozen for a moment). the programs i have running or am currently in doesn't make a difference to this problem. has anyone else had such a problem and figured out how to fix it, or would anyone know what's causing this to happen?

---

### Post by geraldm on 2007-11-10
Every piece of software that writes to the screen has the problem.  It must remove the 
cursor, then write to the screen, then replace the cursor where it should be.  
If it is annoying, or seems like a bug, the program in use may need to improve.

Gerald

---

### Post by battles33 on 2007-11-10
i understand that, however even if i am at the desktop with no programs opened, the same thing happens.

---

