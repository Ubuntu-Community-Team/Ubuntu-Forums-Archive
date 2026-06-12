---
title: "no shutdown button"
date: 2007-11-07
forum: General Help
---

### Post by xjgnsdof on 2007-11-07
I just edited my run level services and suddenly can't see "shutdown" or "restart" button when I select System => Quit. I only have "suspend" and "hibernate" in the bottom row. Anybody know what runlevel script is responsible for these buttons?

---

### Post by xjgnsdof on 2007-11-07
up

---

### Post by wormser on 2007-12-27
I found the answer [here]("http://ubuntuforums.org/showpost.php?p=3935124&postcount=21")!  The solution:

> System-> Administration-> Login window-> Local(tab)

Checked the show actions check box. And it works.

I tested it by unchecking it and lost my quit button.

---

