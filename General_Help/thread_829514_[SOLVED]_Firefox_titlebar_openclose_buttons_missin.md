---
title: "[SOLVED] Firefox titlebar open/close buttons missing in Emerald"
date: 2008-06-14
forum: General Help
---

### Post by Morty007 on 2008-06-14
I know this is a well known bug, and can't seem to find the fix by searching in the forums. I pull up a terminal and do emerald --replace and that will work only if I don't close out the terminal screen. 

If I close out terminal then it will get rid of the close button/titlebar in firefox:(

---

### Post by Morty007 on 2008-06-14
Actually, it every window now, not just firefox:confused:

---

### Post by Morty007 on 2008-06-15
Can anyone help?

---

### Post by techstop on 2008-06-15
It's normally considered poor form to bump your own posts multiple times in one day, however....

Go to ccsm, and then the Window Decoration plugin. In the Command text box, you should have;

```
emerald --replace
```

If not, change it so it is and logout. Press Ctrl + Alt + Backspace to restart X and log back in again. Your problem should be fixed.

For future reference, if you want to run a console command and not have to leave a console window open, press Alt + F2 and enter your console command in the box that appears.

---

