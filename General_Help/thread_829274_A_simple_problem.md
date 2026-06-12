---
title: "A simple problem"
date: 2008-06-14
forum: General Help
---

### Post by TommyIndep on 2008-06-14
Ok, I have a quite embarrassing problem, I created a desktop shortcut to the "home" and the "computer" folders, only now I have no idea how to remove them... Yes I'm sure it's easy to do it, I just don't know how.
Anybody want to explain this to me? :KS
The reason I want to remove them is that I never use them, so much for my "shortcuts", right? :p

Thank you in advance!

---

### Post by Forlong on 2008-06-14
Select them and press the [del] key of your keyboard.
(edit: if you want to delete them completely, press [shift] at the same time)

There should also be an option in the context menu to move them to the trash.

---

### Post by TommyIndep on 2008-06-14
No I tried that already, you know, 'cos it works with every other folder, but not the "home" or the "computer" ones, even the option in the context menu is greyed out so I can't click it.

---

### Post by mike2357 on 2008-06-14
Give this a try:

1.  From a terminal window, run gconf-editor
2.  Navigate to apps/nautilus/desktop
3.  From there, in the right-hand pane, you can check or uncheck boxes for desktop icons as you prefer.
4.  Select File -> Quit.  You should be good to go.

---

### Post by TommyIndep on 2008-06-14
> **mike2357 said:**
> Give this a try:

1.  From a terminal window, run gconf-editor
2.  Navigate to apps/nautilus/desktop
3.  From there, in the right-hand pane, you can check or uncheck boxes for desktop icons as you prefer.
4.  Select File -> Quit.  You should be good to go.

Exactly what I needed! Thanks a lot, mike! :)

---

