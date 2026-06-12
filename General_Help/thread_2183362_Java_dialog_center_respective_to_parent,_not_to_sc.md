---
title: "Java dialog: center respective to parent, not to screen"
date: 2013-10-24
forum: General Help
---

### Post by hojjat on 2013-10-24
I am using a Java program which highly relies on dialog boxes. Every time a dialog box is opened, it is placed in the center of the screen. The problem is I use two side-by-side displays, and the window gets centered in such a way that half of it is in one display, and the other half in the other display.

I was hoping if there would be a way to either force the dialogs to appear in the center of their parent window, or at least in the center of one of the displays, not the whole viewport.

---

### Post by GePBtY7 on 2013-10-25
dialog.setLocationRelativeTo(parent);

---

### Post by hojjat on 2013-10-28
Well I don't have access to the source code of that program. Is there any way I can modify that behavior for a compiled program?

---

