---
title: "Program will not load / yagf"
date: 2014-07-20
forum: General Help
---

### Post by Daniel_Devor on 2014-07-20
A program (YAGF) has been installed and reinstalled using both synaptic and the software center. When first called it promptly displayed but since that time the program will not show on the screen. I am unaware of any other program doing the same thing. Xscan and Iscan both seem to fuction normally . . .just yagf fails to load or display. Help with this problem will be appreciated.

---

### Post by slooksterpsv on 2014-07-20
Try running the app in a terminal, see if it gives you errors. You can also check your  running processes to see if it's running (zombie) via:

```

ps aux | grep yagf

```

If yagf is the name of the executable. If you do find it in terminal via ps aux then you can kill it by taking down its processor number (second column) and typing:
kill *####*

---

